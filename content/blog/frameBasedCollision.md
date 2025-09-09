# Frame-Based Collisions

In January 2025 I started working on a [game for the Boss Rush Game Jam](https://dominik-haas.itch.io/duel-of-shadows) and discovered the [AnimatedSprite](https://github.com/Whitebrim/AnimatedSprite) library which is a state machine based on the [sprite of the playdate sdk](https://sdk.play.date/2.7.4/#C-graphics.sprite) for showing different images of a sprite sheet.

### Animation basics
Going through the documentation I realized it has two great features:
1) it let's you **change the speed** of the animation (tickStep)
2) two you can **compose new animations** out of existing frames

![4 Facets of Animations](https://i.pinimg.com/736x/36/4e/c1/364ec1451d4072190a680dd3e64d6470.jpg)

The tickStep of the animation means for how many "render" frames is a frame of the animation visible on screen. With the reference of the images above, how long to show each single image on the screen. So the higher tickStep to slower is the animation.

To the change the composition of an animation means, you can split up the anticipation, the action and the follow-through frames of an animation into separate parts. Then change the behavior of each part, for example prolong the anticipation to is easier for players to spot an incoming attack.

Here an example were as long as the player holds down the button then ```attackAnticipation``` is played for repeated spinning, then once release the ```attackSweep``` is played. Because the anticipation is only two frames it's slower then the rest of the animation:

<pre><code class="language-json">
  {
    "name": "attackAnticipation",
    "tickStep": 4,
    "frames": [1,2],
  },
  {
    "name": "attackSweep",
    "tickStep": 2,
    "frames": [3,4,5,6,7,8,9],
  },
</code></pre>


See it in action at the end, when when the little character spins the blades then sweeps in with an attack:

![Hold to Spin](https://img.itch.zone/aW1hZ2UvMzI4OTQ5NS8xOTYzNDI3My5naWY=/original/ebU7nq.gif)


These features of the AnimatedSprite are a great fit for me because I wanted to use animations from [Penusbmic](https://penusbmic.itch.io/) for my game jam game and have fine-grained control to use them in various ways.

![Attack animation](https://img.itch.zone/aW1nLzEzNjg4NzcxLmdpZg==/original/b0kmR8.gif)

This example shows the actual hit of the whole attack animations are happening only in a few frames and only then collisions for an attack can be triggered.
And with this image, it's only a single frame:

![Attack animation](https://img.itch.zone/aW1nLzIyNDY2OTMwLnBuZw==/original/F9beFo.png)

I've tried counting the frames and timing the collision with a frameTimer kinda like this:

<pre><code class="language-lua">
function enableCollisionWithReset(player, initialFramesDelay, framesUntilReset)
  frameTimer.new(initialFramesDelay,
    function ()
      -- enable collision
      player.attackRect:setCollisionsEnabled(true)

      frameTimer.new(framesUntilReset,
        function ()
          -- disable collision
          player.attackRect:setCollisionsEnabled(false)
        end
      )
    end
  )
end
</code></pre>

Even if I would land the exact timing, it's not an approach that can scale. I would need a more precise solution, something like a **frame hook**!
In javascript frameworks (vue or react) a hook is referred to binding an event to a certain trigger. Simplest example, you want a certain function to be called an a button is clicked.

### Frame Hook
Apparently it already has **event triggers** for ```onFrameChangedEvent```, ```onStateChangedEvent``` and some more. But these weren't during the animation itself. 

I had to dig deeper and look into the code of the AnimatedSprite library. For our context ```AnimatedSprite:updateAnimation()``` and the ```local function processAnimation(self)``` are relevant. So two main things are happening in these functions, check if the animation needs to advance to the next frame and check if an existing event has to be triggered.

With this uncovered I would still need to implement two things:
1) **Mark the frames** when the collision should happen
2) Find a way to **trigger the collision** event when at a marked
3) **Assign event** per animation to trigger the collision (enable and disable it again)


#### The 1st part is easy

Add it into the json definitions of the animations:

<pre><code class="language-json">
  {
    "name": "attackAnticipation",
    "tickStep": 4,
    "frames": [1,2],
    "sfxFrames": [1]
  },
  {
    "name": "attackSweep",
    "tickStep": 2,
    "frames": [3,4,5,6,7,8,9],
    "collisionFrames": [6,7,8],
    "sfxFrames": [3]
  },
</code></pre>

#### The 2nd part kinda hard

In the depth of the AnimatedSprite, once the number of the ```_currentFrame``` is part of the ```markedFrames``` ("collisionFrames") then execute the ```callback()```

<pre><code class="language-lua">
local function checkMarkedFrames(self, state, markedFrames, callback)
  if (markedFrames == nil or state.frames == nil
   or markedFrames == nil or callback == nil) then
    return
  end

  local actualAnimationFrameNumber = state.frames[self._currentFrame]
  local isMarkedFrame = isInTable(markedFrames, actualAnimationFrameNumber)

  if (isMarkedFrame) then
    callback(self)
  end
end

-- call it like this during processAnimation()
	checkMarkedFrames(self, state, state.collisionFrames, state.onFrameCollisionEvent)
	checkMarkedFrames(self, state, state.sfxFrames, state.onFrameSfxEvent)
</code></pre>


#### The 3rd part

Is okay I guess:

<pre><code class="language-lua">
function activateCollWithFrameCooldown(attackRect, cooldownFrames)

  if(not attackRect:collisionsEnabled()) then
    -- active the collision
    attackRect:setCollisionsEnabled(true)

    if (DEBUG == true) then
      local visibleImg = getHitRectImage(attackRect.width, attackRect.height, true);
      attackRect:setImage(visibleImg)
    end

    frameTimer.new(cooldownFrames,
      function ()
        -- disable the collision
        attackRect:setCollisionsEnabled(false)

        if (DEBUG == true) then
          local clearImg = getHitRectImage(attackRect.width, attackRect.height, false);
          attackRect:setImage(clearImg)
        end

      end
    )

  end
end

-- the state is the current animation, multiple the amount of collisionFrame entries
-- with the tickStep to get the duration (in frames) the collision has to stay active
local state = animationSprite:getCurrentState()
local cooldownFrames = #state.collisionFrames * state.tickStep

-- the attackRect is an empty sprite with setCollideRect() set
activateCollWithFrameCooldown(attackRect, cooldownFrames)
</code></pre>

#### And here in action

![Slowmo Testing](https://img.itch.zone/aW1nLzIyMzE0MzY5LmdpZg==/x150/z%2FedFV.gif)

The collision doesn't always work here because of the slow motion testing, but I wanted to show this because you can also see the debug rect being visible when the collisions are active. And also slow motion is possible when turning up the tickStep :)

I think that's it for now. Let me know in the comment, if you also like to see the code to check the collision once the "attackRect" is active?

PS: I created a pull request for the integration of the the ```onFrameCollisionEvent``` and ```onFrameSfxEvent```, so if you have the latest version of AnimatedSprite you can use it has described.

Cheers!
