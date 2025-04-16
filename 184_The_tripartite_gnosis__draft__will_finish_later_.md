# The tripartite gnosis (draft, will finish later)

**Author:** ~hastuc-dibtux  
**Date:** 2024-06-10 21:09:45  
**ID:** 170.141.184.506.844.998.496.735.974.843.098.333.184  
**Replies:** 0  

---

### 

Our shrubbery is divided into three parts:


* The %dirt (shrub runtime)

* The %vine (privileged "root shrubs")

* The %bush (regular shrubs)


We shall start at the top and work our way downwards. 


### Surf's Up

A %bush is a regular shrub. It maintains state, and receives %pokes. It is a combination Pizza Hut, database table, RPC endpoint, smart contract, Plan9 file, smalltalk object and Taco Bell.
%bushes cannot, by construction, do anything that is not referentially transparent, create evil vases or violate causality. As such, most code that fits in today's notion of "userspace" should be plain old kooks.
The lawful nature of a bush lends it well to aggressive sandboxing. With reasonable security policies (more later), it is perfectly viable to download and run untrusted code in a sandbox, which may itself download and run more untrusted code in a smaller sandbox, ($TONKA when?).
It's "conceptual" interface is simply:


```hoon
|%
::  +state: State of the shrub
++  state  *pail:neo
::  +poke: Pokes that are accepted by the shrub
++  poke  *(set stud:neo)
++  on-poke
  |=  [old=pail:neo pok=pail:neo]
  ^-  pail:neo
--
```

Note that this interface specification elides +deps and +kids, in addition to removing the +state $curb. This is because those are not "externally facing" interface. i.e. any arbitrary consumer of this shrub only cares about its +state and +poke.
Indeed, +kids and +deps in our current model are not immutable properties of the shrubbery notion of a $bush, but are implementation details of a tangled growth underneath our feet.


### Vineland, in the last instance

Behold, the abstraction infesting everything you love. Beside, underneath, betwixt, the %vine is everywhere and nowhere.
Vines are the "chroot" concept from an earlier screed, but with a far cooler (and four letter) name. Vines are everything that could be pulled out of %dirt and made swappable.  
The "bush model" for instance, lives in the %vine. $kook, as currently defined, is one such $bush. Dependencies and "capturing" of children are not natural laws of the land, but the rules of men. The $card (or any other description of an attempt of a bush to perform IO), is entirely up to the vine to decide what it looks like. Vines may also inspect and rewrite cards if they wish. This allows functionality like universal logging and crash reporting, in addition to fancier tricks like %ns-resign-first-responder (only partly kidding). 
%vines should include a security model in their bushes. All calls and pokes take a `$wine` which is simply


```hoon
|%
+$  wine
  $%  [%open ~]
      [%chum =pith]
      [%shut key=@uvJ]
  ==
--
```

All pokes and peeks into any of the bushes on this vine are from a $wine. The vine may reject or accept a poke or peek based on a wine. 
To be clear, I'm not diminishing any of the work done with the call stack ordering, or the %gift or the capturing system. A well-functioning %vine should have either those things exactly, or workable replacements. 
Vines are also BYO build system, which means that the type of type and therefore vases, may be different in different root shrubs. (TBA: elaborate)
Our vine interface (very, very, TBD):


```hoon
|%
+$  bush-gift
  $%  [%grew =pail:neo]
      [%dead ~]
  ==
+$  task
  $%  [%cork p=pith q=wine r=(set stud:neo)] :: ask for permissions
      [%bush p=pith q=bush-gift] :: hear that one of it's bushes did something
  ==
+$  gift
  $%  [%bush p=pith q=bush-gift] :: tell bush did something
      [%bung p=pith q=(unit signature)]
  ==
+$  state  !!
```

### Dust to dust...

The dirt is our shrub "runtime": currently app/neo, soon a vane, eventually arvo itself. The dirt has two jobs:


* Coordinating %vines 

* Maintaining referential transparency


