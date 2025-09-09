# Character Reveal: Samurai


The second character to be playable [Duel of Shadows](https://dominik-haas.itch.io/duel-of-shadows) is the Samurai!


### Skills

The Samurai has a strong attack which can be combined with a stronger follow up attack. The later has a strong knock back effect to the opponents. As a second skills the Samurai can block with its huge sword.

![Reveal Samurai](https://img.itch.zone/aW1hZ2UvMzI4OTQ5NS8yMjg4MzAwOS5naWY=/794x1000/wdpP%2FR.gif)



The Samurai is the beefy contrast to the quick, agile Assassin. With slower movement, heaver attacks with knockback and a block skill.
While attacking its possible to do a second combo attack which deals more damage and has more knockback. The block can interrupt a on going attack sequence.

### Refactoring

I had to do some major refactoring to be able to re-use most of the code of the character controller for the second character. I've isolated the code which has to do with skills, meaning logic for playing animations, activating collision rectangles and waiting for the cooldown.

I tried to combine the different skills I had for the Assassin and the Samurai, but I realized it is a classic case for a decorator pattern. (In Software Engineering this is refereed to a mechanism to add functionality in a structured way ) So I've took it apart of be able to handle the different these cases separately. The base skill and then the charing of the Assassins attack.
Which is something I consider **one of the most important aspect in programming**! So why didn't do that from the start? ;)

Sometimes you need to go through the process to figure out which cases require different logic. And it depends on how much code is needed to reflect a certain logic. The more code you have to higher the cognitive load to manage it, the more it makes sense to separate it.

### Game Design

I've defined a concept which allowed me to cleared select characters and define their skills. It is not very strict, but I've had a look at various characters and their skills, grouped them and picked what would fit in a focused concept. One major defining factor will be if I can port the character art to 1-bit in a way, that it still looks good on the playdate.


#### To Be Defined

In terms of implementation for these two characters, there is still two things I'm not clear yet: **knockback** and **jumping**.

- Kockback implemented with velocity or in general with physics, would allow for an easier combining of different kockback forces ex. for a combo attack
- Jumping is something I intuitively wanted to do when playing. Especially with the Assassin because already it feels nimble to play it.

But until now there is no way jumping would benefit anything. No platforms, nothing to jump on or over. So nothing to dodge really... even if it would be used to jump over projectiles or a boss, the implementation requires a lot of effort. Gravity, velocity and a lot of tweaking until a jump really feels good.

So the effort would have to be worth it. Then again, having physics for objects, could be make the game feel alive and give the knockback of skills more meaning. A knockback or push of an object could also happen on the y-axis, which would make an attack feel more impactful. An objects could also be used to push for a ranged attack


## What's Next?

Next up finishing the **swap skill!**

Probably in a first version not as envisioned, with the slow motion and the circular menu to choose characters. I do like that vision but in the end needs to be sense how it feels to do it. So in the first version there will be a swap between Assassin and Samurai.

After that, it's time to refactor the boss implementation for scaling for different variations of bosses. Once a second boss is playable, it's time for a demo release!
