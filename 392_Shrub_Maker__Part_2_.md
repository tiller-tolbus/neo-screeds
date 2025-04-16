# Shrub Maker (Part 2)

**Author:** ~hanfel-dovned  
**Date:** 2024-05-07 11:01:59  
**ID:** 170.141.184.506.790.136.669.389.728.716.414.779.392  
**Replies:** 6  

---

Last week `~risruc-habteb` posted a mockup of a MUD running in Sky, and people got excited. I've never played an actual multiplayer MUD myself, but thinking about the design of text-based adventure games in Shrubbery has been surprisingly fruitful.
I'm a massive Zelda enjoyer, and I would claim that the vast majority of their non-text-based puzzles (even their beautiful [puzzle box dungeons](https://www.youtube.com/watch?v=pwHqY_4nsJ4)) are reducible to a tree of nodes. The properties of space that these puzzles are concerned with have more to do with navigating lock-and-key structures and less to do with, say, [parsing objects moving at different velocities.](https://warpzone.substack.com/p/super-mario-bros-3-is-the-perfect)


Assume that any object's state can be represented with a bool, and that any object can have up to two dependencies. The object also has a set of rules that dictate how its state changes in relation to its dependencies and user input.
+$ element [status=? poke-logic dep-logic]
+$ poke-logic (set option)
+$ option $%(%flip %once %if-deps)
+$ dep-logic $%(%none %mirror %inverse %and %nand %or %xor)
The statue in this image has two potential states: "on the left button" and "on the right button." Its poke-logic is %flip, meaning that when you poke it, it toggles between these two states. One button's dep-logic is %mirror, and the other's is %inverse; both doors' dep-logic is %mirror. You move the statue onto the left button, "obtain" the key (which in reality simply flips its state, which the chest depends on), move the statue onto the right button, and unlock the chest.
Using enough of these logic gates, I believe you can build up to any puzzle-like situation of any complexity. Dress this up with some flavor text, and you can make this feel really natural.
imp/mud-entity 
++ state = [name=@t on-description=@t off-description=@t]
++ kids = element
Of course, these don't need to be logic gates. You could write a game in Shrubbery where every element has a very bespoke set of logic and arbitrarily many dependencies. But to make this usable for non-programmers, a limited set of options that can still be combined into arbitrary complexity is ideal. A UI for creating your own MUD would have a few input fields for text descriptions and some dropdowns for choosing their behaviors and dependencies.
With these building blocks in place, there's a realization to be had: these elements can be generalized to much more than just video games:
imp/pixel-obj
++kids = [element, rectangle, rectangle]
:: con file grabs the rectangle that corresponds to status.element
:: poke.clickable.rectangle can route to this /element 
We can plug these elements into the renderer from Shrub Maker (Part 1) to let users build out full-stack programs without writing any code.
- You can draw a simple sprite.
- You can draw a clickable sprite that pokes some other shrub.
- You can draw a clickable sprite with two rectangles, where clicking pokes yourself and flips between the two.
- You can draw a clickable sprite with two rectangles, where clicking pokes some other shrub, which this object's element ultimately depends on and therefore will be flipped by.



## Replies

### Reply from ~hanfel-dovned on 2024-05-08 14:45:44

[https://twitter.com/eshear/status/1787881174095822906](https://twitter.com/eshear/status/1787881174095822906)


---

### Reply from ~hanfel-dovned on 2024-05-07 11:25:03

As dorky as it is to come up with an "official definition" for a game genre, I find the [Berlin Interpretation](https://www.roguebasin.com/index.php/Berlin_Interpretation) to be a pretty good representation.


---

### Reply from ~risruc-habteb on 2024-05-07 11:23:33

in the current era, the defining feature of a "rogue-like" is a single life per play, with a certain amount of press-your-luck and permadeath.  (to my taste -- there is some debate about this point)


---

### Reply from ~hanfel-dovned on 2024-05-07 11:20:28

I was thinking that what you mocked up was a text adventure. Roguelikes are more about systemic interactions emerging from pre-defined entities that get re-used over and over, whereas adventure games are more about one-off entities creating one-off situations. I always assumed a MUD was a sort of blend of the two genres with multiplayer thrown in, but I'm realizing now that I don't think I've ever played a text-based systemic game...


---

### Reply from ~risruc-habteb on 2024-05-07 11:18:03

some prior art here:
[https://github.com/Fang-/suite/blob/master/app/bard.hoon#L574](https://github.com/Fang-/suite/blob/master/app/bard.hoon#L574)

simple enough markup(could be plain old xml), but allows creation of interactive stories of arbitrary complexity


---

### Reply from ~risruc-habteb on 2024-05-07 11:14:55

for the sake of precision, the mockup was technically a rogue-like, not a MUD(multi-user dungeon).  i've actually not played a MUD and i have a difficult time imagining how to build one well (from a game design perspective).  I have more experience with various rogue-likes and think of that as the appropriate first target here.

true, and i think for phase 1, good enough to have users write their games/stories/apps in a simple markup language which is compiled/parsed to shrubs.


---

