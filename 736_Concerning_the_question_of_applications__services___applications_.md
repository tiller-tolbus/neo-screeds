# Concerning the question of applications (services & applications)

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-26 15:51:52  
**ID:** 170.141.184.506.772.925.721.321.815.594.799.988.736  
**Replies:** 12  

---

**Service discovery**


* Current shrubbery has no idea what an application is. This is largely because we have no need for notions of applications, as they would introduce a heterogeneity into the namespace that would defeat the point.

  However, the notion of an application is useful to us, from the perspective of service discovery. An application is a mapping from user intent to the software that fulfills that intent. However, this intent is difficult to concretize in any meaningful way, because the underlying implementation could vary dramatically. Let’s call these intents “accords”. An “accord” is just a text file living at /[desk]/src/acc/[name].txt. (this allows us to use $stud Similarly to our role system, this is to contain exclusively English text, describing what the accord is). Some examples of accords:

  * %chat (user wants to talk to user)

  * %wallet (user wants to send money to user)

  * %call (user wants to call user)

  * %notify (developer wants to notify user)

  * Etc.

* One could consider the idea of an $accord to be more or less a semantic, namespaced port (like the IP port) that multiple applications can bind to

* Here we cover the notion of defaults as simply (jar stud [pith slip imp=stud]), this is called an $atlas (a $slip is just the type that describes the api of the shrub)

* The user is free to add and reorder these defaults

* When a user or developer wants to interact with a user with some intent, they retrieve the $atlas for that ship.

* We provide standard functions for checking the conformance of the $slip in the atlas with the required $quay.

  In general we have some rules for querying $atlas

  * Exact match (i.e. matching implementations) should be preferred almost always

    Else, pick the first item in the list that conforms to the required $quay.

    * In this case, the shrub should warn that the connection between shrubs is not an exact match, and certain constraints of the shrub may be violated. e.g. Disappearing messages, etc. (if the kernel lies, this is unenforceable, but just don’t be friends with such unscrupulous individuals (zk also an option here))

* We gather a foreign ships $atlas as part of the handshake process when a ship becomes our peer, and remain subscribed to them until the ship breaches

* We are also very much interested in our own atlas, because it allows 


## Implementation

Our global state of known $atlases is a `+$  globe  (map ship atlas)`
bound at /globe , and individual atlases at /globe/[ship]
The implementation wrinkle here is mostly ergonomic. We would like to know about more or less every ship's atlas, but we do not want to depend on it, because that would wake every shrub on every ship up every time somebody changes their default chat application.  In general, we don't care about diffs on atlases, because we should only use them for initiating communication. If the user changes their default chat application, that should not retrigger all the chats to migrate to the new default


* One option is to put it in the bowl. This seems straightforward and uncontroversial. It is possibly an enormous data structure, so maybe not. This also does not address the question of discovering new peers, but perhaps this could be solved by a poke to /globe

* The wildcard option is to revive dotket, but only for $atlases. This makes our subject significantly smaller. Additionally, because it is only being used for an edge case, then the remaining questions about dotket are easier to deal with. The blocking semantics of dotket could be revived in order to address the notion of discovering an endpoint



## Replies

### Reply from ~midlev-mindyr on 2024-04-29 11:17:39

Well yes, the sender would have to include information about the interface it requires in addition to the accord.
As for security, I don't think your example holds up. What's stopping me from implementing my own chat client which spoofs the disappearing message client but actually saves everything?
More broadly, the shrub may want to disregard the user's preferences, but ultimately the user can rename or spoof things however they want, and there's not much the shrub can do about it, right?

When I send a request to a server on a port, I don't get a list of process ids and choose which one I want to talk to, I trust that the server is configured properly to know how to interpret my request on that port. If accords are like ports, then perhaps we treat them in a similar way. Except we need more than an a simple identifier, like a port number or accord text, because we also need to specify what sort of interface we need.

Separate question: Can we scry on an accord, like `/accord/chat/messages/all`? (probably the structure of this is way off, but you know what I mean I hope). I suppose to maintain referential transparency we'd need to version the atlas or something, idk


---

### Reply from ~hastuc-dibtux on 2024-04-28 11:20:58

the user can set their preferences (the ordering of the entries in the atlas), however it is in the general case impossible to constrain accords on the receiver side as you suggest for a couple of reasons:
- because the accord implies nothing about the implementation, the shrub on the sender side necessarily must use a shrub whose implementation it can speak
- certain shrubs may want to avoid the user's first set preference for a variety of reasons. For instance, consider a disappearing message client with time-bounded signatures. The receiver should not be able to force such a message into a traditional persistent chat client, because that would be a violation of the security guarantees that the sender requires. It could however, use the user's first set chat client to send them a message that they want to contact them over the disappearing chat. 

This isn't the be and and end-all however, because you can imagine overlay shrubs that add additional type signatures for the same underlying chat client. Moreover, the polymorphism allowed in the user interface also lets you just aggregate disparate chat implementations inside the same window, thus the specific implementation that any given chat is using is basically irrelevant from the perspective of the user


---

### Reply from ~hastuc-dibtux on 2024-04-28 11:11:58

given the design of shrubbery so far a service discovery layer like this is unavoidable


---

### Reply from ~midlev-mindyr on 2024-04-27 21:48:29

I'm very new to shrubbery and don't have the full picture yet, so sorry if I'm missing the mark here.
It seems like trying to share atlas data and know atlas data is a lot of work and complexity that we should avoid if possible.
If I'm sending someone a %chat, shouldn't *they* be the one to decide which shrub handles it? If they update to a new %chat app, shouldn't *they* be the one to decide whether existing chats are moved over, or which ones?
Not that this is simple to do either, but perhaps I can just send a poke to an accord along with some context about what I'm trying to do, and the recipient (either myself or someone else) interprets that and routes it to the correct shrub based on user defaults and specific overrides.
This implies a whole system for managing shrub<->accord connections and priorities, but at least that's all done locally and we don't have to scry about it from the shrub or subscribe to an atlas for every peer.


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:44:30

it does matter over the network though, and we should always be careful not to introduce latency into the initial interaction with another ship


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:43:17

size of noun doesn't matter for putting in bowl, "they're just pointers Leon"


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:42:21

do we really want a whole atlas for another ship? I would think we only want the accords that are relevant for some particular shrub on my ship, not all accords for all apps


---

### Reply from ~fabled-faster on 2024-04-27 17:42:02

Semantic ports 🫨🤯


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:36:23

... because it allows what?


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:36:13

*This post appears to have malformed or incomplete content in the original JSON file.*

---

### Reply from ~rovnys-ricfer on 2024-04-27 17:35:21

basadissimo


---

### Reply from ~rovnys-ricfer on 2024-04-27 17:35:14

*This post appears to have malformed or incomplete content in the original JSON file.*

---

