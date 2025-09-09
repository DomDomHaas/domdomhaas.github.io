# DevBlog: Aftermath of the Boss Rush Game Jam 2025

## Thank You Very Much

First of all, I want to thank everyone who downloaded and played Duels of Shadows.

Here are the statistics for February: 

![Game Stats](https://img.itch.zone/aW1nLzIwMTI0MTY0LnBuZw==/original/5lNOdM.png)

I didn't expect to reach 160 downloads—this is great!
Even 9 people were willing to pay for it—thank you so much!
I've invested the money into research: 

![Book Order](https://img.itch.zone/aW1nLzIwMTI0Mjg4LnBuZw==/original/TgM479.png)

It is important for me to get comments, suggestions, and feedback about the gameplay from players.
Thank you very much—please keep them coming! 😊

I’ve really enjoyed working on Duels of Shadows, and receiving this feedback has given me the motivation to continue development.
I’m a father of two kids, and my job as a software engineer is challenging, which means I don’t have much leisure time. Because of this, I’ve explored some options to reduce my workload and spend more time developing this game. However, for various reasons, it’s not possible at the moment.


## Progress

Nonetheless, I keep working on the boss-rush game Duels of Shadows—by the way, this title will probably change.
I have different ideas for the story, bosses, and levels, so the title will evolve to reflect that.

As mentioned, I’m researching different variations of boss fights.
I’ve found some interesting videos on YouTube, mostly on the analytical and design side rather than direct development. However, they provide great insight into the full spectrum of what boss fights offer as a gaming experience.

I’ve also found two podcasts that I really enjoyed.

Do you know of any other resources?
Which games have had boss fights that you enjoyed? Why?
And do you have a favorite boss fight?

## Conception

IMHO, the current state of the game could be considered a proof of concept. The next step is a prototype on the way to a minimum viable product, and then full production.

![Software States on Pinterest](https://i.pinimg.com/736x/eb/20/54/eb205431cebf6cb54cc96c63a15ea366.jpg)
[Software States on Pinterest](https://www.pinterest.com/pin/336433034674663245/)

There are different models for defining the state of a software product.
For games, having a demo at a certain point is often important. A vertical slice can be valuable when reaching out to publishers—it ideally showcases a game’s potential but isn’t fully scaled out. Depending on the game, this can be difficult to achieve because it requires most, if not all, of the systems to be implemented at a certain level of quality.

This is different from a demo, where the player might experience the first part of the game, but not all mechanics and levels need to be implemented. The level progression in a demo is often tailored for a short experience, whereas a vertical slice gives a general impression of the finished game.  

That said, I’m honestly not sure how often vertical slices are used by publishers, as I can only speak from my experience during the development of [DERU](https://inkkit.itch.io/deru). 


Conceptually, my next step is to define the core game mechanics more clearly and refine how to deliver a great player experience. Once my research provides more insight into boss fight structures and progression, the next big step will be designing a concept that scales the game through the phases I mentioned earlier—and possibly beyond.

This means defining how many bosses and playable characters to create, their variations, and how the player progresses through the game.

## Programming

I’ve been working on refactoring the code structure from the game jam version to make it more scalable.
My goal is to add new characters and bosses without duplicating code while keeping shared functionality intact.

This approach will make it easier to have multiple bosses share mechanics while still allowing for unique features in certain bosses.

The same applies to player characters—they will share a lot of functionality. As mentioned earlier, the extent of this is still unclear, but I’m fairly certain I’ll go for character variations with different moves, rather than introducing items for a single character.

Additionally, I want to experiment with swapping characters mid-game, somewhat like in a tag-fighting game. (Street Fighter EX3, Marvel vs. Capcom, or 2XKO).

![Character Swap](https://img.itch.zone/aW1nLzIwMTI0NTA3LmdpZg==/original/E86uG%2B.gif)


It will probably just a tiny aspect, but I'm excited about this perspective, mixing a boss rusher with a little sprinkling of fight mechanics? Sounds good to me :D

If you made it this far, thanks so much! And let me know in the comment what do you think?


**EDIT**: While I'm happy with the progress of the game jam version, I'm not super happy with the behaviour of the current boss "Shadow Of Storms" yet. It was a pretty simple implementation of a few different behaviours. I'll see how to improve this boss fight as well.

Thanks for reading!

(Originally posted: <https://dominik-haas.itch.io/duel-of-shadows/devlog/898719/aftermath-of-the-boss-rush-game-jam-2025>)
