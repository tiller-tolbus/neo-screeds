# potential forwarding on doubly virtual shrubs

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-26 13:24:42  
**ID:** 170.141.184.506.772.762.821.107.972.468.929.200.128  
**Replies:** 10  

---

Consider:
Add a `+poke` arm to overlay namespace implementations that is a `(set stud)` 
Add a `+forward` arm to the implementation that is `$-([our=ship deps=* args=(pole iota) inner=pith:neo =cane:neo pail:neo] pail:neo) :: deps elided for brevity`
Then you could poke on the overlay, and possibly unwrap or transform pokes before the overlay forwards it onto the overlaid shrub
idk, just an idea



## Replies

### Reply from ~hastuc-dibtux on 2024-04-29 16:26:58

slightly more questionable on allowing overlays to transform their pokes


---

### Reply from ~hastuc-dibtux on 2024-04-29 16:25:24

APPROVED!


---

### Reply from ~hastuc-dibtux on 2024-04-29 16:25:17

ok so turns out actually allowing forwarding on doubly overlay shrubs produces less path inspection than not allowing it


---

### Reply from ~hastuc-dibtux on 2024-04-26 15:53:40

there's an analogue of "don't inspect your duct" for shrubbery, which is "don't inspect your paths" (except for children, obvs). So, either you rewrite src.bowl for the ack, or you don't. If you do, you are required to know that you're poking into an overlay namespace, which seems suspect. If you don't then it's fine, but idk


---

### Reply from ~rovnys-ricfer on 2024-04-26 15:46:22

`~migrev-dolseg`: ok this is a cool idea... maybe I could be convinced about poke overlays being a good idea


---

### Reply from ~tiller-tolbus on 2024-04-26 15:44:04

I like it. it is basically just an overlay on the poke namespace. it can only overlay existing pokes, but the idea is that a poke might mean something else if done from the context of an overlay namespace. 


---

### Reply from ~rovnys-ricfer on 2024-04-26 14:27:18

FWIW I'm skeptical of supporting writes to overlays, in general. It makes it harder to understand what's what.  I'm not sure I understand fully what you mean here though


---

### Reply from ~migrev-dolseg on 2024-04-26 13:49:53

ah yes, the old "there's a shrub for that" strategy.


---

### Reply from ~hastuc-dibtux on 2024-04-26 13:47:53

It doesn't if you pull HTTP serving out into it's own shrub


---

### Reply from ~migrev-dolseg on 2024-04-26 13:47:01

%sky becomes an overlay namespace which acts as an http request handler for your namespace. transforming and un/wrapping htmx into http requests/responses. i believe this still requires that app/neo have the assumption that POST=poke, PUT=%make, and DELETE=%tomb


---

