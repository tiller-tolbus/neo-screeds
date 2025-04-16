# Shrub Maker (Part 1)

**Author:** ~hanfel-dovned  
**Date:** 2024-05-06 15:51:14  
**ID:** 170.141.184.506.788.863.072.476.754.947.497.525.248  
**Replies:** 15  

---

`~migrev-dolseg` builds some incredible things in sky. This is mainly because ~migrev-dolseg is an incredible developer. The rest of us grug-brains who aren't capable of reasoning about flexboxes might need something simpler.
This is where I return to first principles: why can't I just draw a pixel to the screen? It's inhumane to make people draw rectangles by typing out `drawRectangle(0, 0, 40, 50, 0x123456)` when they just want to take a stylus and draw a rectangle.
"But what about responsiveness??" My *response* is that resizable browser windows may have been the single most expensive design decision in human history. Drawing color values directly to specific coordinates within a space that has a consistent aspect ratio works just fine for game developers.
(Side note: I began typing this post out within the Groups notebook, and then when I moved my window to another monitor, everything got deleted and I'm now writing this for the second time. Isn't web browser *responsiveness* great?)
In the spirit of tackling native UI from a completely different angle, I wrote a [pixel-based UI renderer in shrubbery](https://github.com/urbit/shrub/tree/shrub-maker). Its fundamental building block is the `rectangle`.
`$: width=@ud`` height=@ud`` pixels=(list @ux)``==`
A `screen` has many rectangles as children. A renderer loops over a screen's kids and draws them.
Right now I do this in sky using an HTML table.
You could imagine building a desktop app that uses %lick to get these values out.


So what will user input look like? For this, we will add one more field to the rectangle type:
`$: width=@ud height=@ud pixels=(list @ux) clickable=(unit [=action (list (unit @ux))])==  +$ action  $% [%post =pail:neo] :: [%form =stud:neo ???] :: {pre-filled vase parameters + prompt for user input}==`
A `clickable` is a set of pixels within a rectangle that, when moused over, change color to signify clickability. A clickable region has a pre-defined `action` associated with it. This action can either immediately send a completely pre-defined poke, or it can spawn an input form that requests some text from the user. These input forms don't need to be defined by the developer of the UI; these should be system-level affordances, provided either by sky or the browser itself, that render as pop-ups or sidebars. Once again: this works just fine for game developers. Most people are barely literate anyway, why assume that they want to type words all the time?


The beauty of this is that it makes UIs not just easy enough for any developer to create, but for any power user to create themselves. You draw your UI, draw a second layer over it for buttons, wire those buttons up to some specific shrubs via a UI similar to accel, and you publish.
All that's missing is an easy way for people to create their own no-code backend logic. That's where the MUD ENGINE comes in.



## Replies

### Reply from ~winter-paches on 2024-05-10 09:31:23

Here's my screed: HTML was never designed to be a hi fidelity visual data representation. Indeed, to the contrary, it was intended to be the lowest common denominator for transmitting platform neutral text content which could be**lightly** styled. It follows that the emergence of the web browser as an universal, graphical, overlay OS was never intended and indeed has only been accomplished by layering on layer after layer after layer of shit. And note that it hasn't even succeeded in this as "This works best in Browser X" attests to. In short, a disaster. We need to **return** to what was always the proper way to do this.


---

### Reply from ~winter-paches on 2024-05-10 09:03:51

be encouraged that that was initially developed 30 years ago and is still available today. The good ideas never go away they sometimes are just forgotten. 


---

### Reply from ~winter-paches on 2024-05-10 09:00:06

i'll just leave this here for reference: [https://wiki.squeak.org/squeak/30](https://wiki.squeak.org/squeak/30)


---

### Reply from ~ripwen-sabrup on 2024-05-10 05:39:20

what is sky?


---

### Reply from ~sivrul-litsub on 2024-05-07 13:59:44

`~hanfel-dovned`: It's the TUI project that I had showed you. Homunculus treats characters like pixels — the logic is the same.


---

### Reply from ~nospur-sontud on 2024-05-07 12:25:52

iam i weird that i like flexbox? 


---

### Reply from ~risruc-habteb on 2024-05-07 08:59:50

[https://github.com/R-JG/homunculus/](https://github.com/R-JG/homunculus/blob/master/desk/app/homunculus.hoon)


---

### Reply from ~hanfel-dovned on 2024-05-07 08:45:21

`~sivrul-litsub` oh sweet, got a link?


---

### Reply from ~sivrul-litsub on 2024-05-07 02:19:51

Yo `~hanfel-dovned` my current project is basically 3500 lines of pixel rendering logic in Hoon. I'm down to collaborate


---

### Reply from ~hastuc-dibtux on 2024-05-06 18:57:48

fuck yes!


---

### Reply from ~fabled-faster on 2024-05-06 17:29:08

Shrub willing, we can shed the browser like an old exoskeleton soon


---

### Reply from ~hanfel-dovned on 2024-05-06 17:17:07

`~fabled-faster` Thank you! Sorry for the snarky public bug report. I really do get the impression that the browser just makes everyone's lives unnecessarily difficult, I don't envy your uphill battle.


---

### Reply from ~fabled-faster on 2024-05-06 17:07:06

`~hanfel-dovned` heard on the notebook bug, sorry about your loss of text — forwarding this to people who can fix it 


---

### Reply from ~tiller-tolbus on 2024-05-06 16:45:00

Lmao. based. 


---

### Reply from ~risruc-habteb on 2024-05-06 16:05:44

love this angle of attack


---

