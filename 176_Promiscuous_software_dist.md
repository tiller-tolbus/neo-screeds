# Promiscuous software dist

**Author:** ~hastuc-dibtux  
**Date:** 2024-07-10 17:29:40  
**ID:** 170.141.184.506.892.568.858.172.773.939.256.754.176  
**Replies:** 6  

---

**Promiscuous software distribution**
All current modes of software distribution are deeply broken and MUST DIE. The only one that works for the average end user is, quite hilariously, javascript. What makes the web great is the total lack of friction with running untrusted software on somebody else’s computer. “Installing software” is a solution to a problem that no longer exists. The only place where the average user “installs software” in the traditional sense, is the App Stores of apple/microsoft/google. The megacorp middleman exists purely to provide oversight to enforce that developers don’t do stupid or malicious shit (see: [https://www.schneier.com/blog/archives/2012/12/feudal_sec.html](https://www.schneier.com/blog/archives/2012/12/feudal_sec.html)) But what happens when the oversight goes rogue ([https://x.com/lcasdev/status/1810696257137959018](https://x.com/lcasdev/status/1810696257137959018))? Requiring the user to make manual decisions about software that they can’t read is doomed to failure. Because shrubbery has no concept of “application”, we never actually have to actually install software. Instead we can just exchange bodily fluids (code) with anybody who has them. We can hear about code in a variety of ways, over gossip, by attempting to synchronize a foreign namespace, or find it on the side of the road.


# In the beginning, there were types

Types (and the code used to render them) are more or less trivial to sandbox. Wrap all foreign type manipulation in a %jinx hint, and you’re done. Therefore, the way promiscuous software distribution handles types is that if it sees a stud it doesn’t know how to handle, it will download it and run it immediately, totally invisible to the user. This allows users to do extremely organic software discovery. They can be using a chat application, and somebody could send them an excerpt from a data analytics suite, and the suite will be downloaded as part of message receipt, allowing them to use the data analytics suite inside the chat application. The code for the data analytics suite is not yet interacting with any part of the user’s own namespace, but just being used to synchronize and mirror data.


# The shrub itself

Shrub implementations are also trivial to sandbox, under one condition: They must not take any dependencies. Software that has never been explicitly marked as trusted can be created anywhere in the namespace, but is not allowed to take any dependencies.
With the above two policies, we have feature parity with javascript.
Thus, the idea of “installing” software is relegated to marking it as trusted. Come back next week when we automate the trust process.



## Replies

### Reply from ~hastyp-patmud on 2024-07-11 11:05:53

CC: `~doplyr-harbur` seems like we should be positioned to help with part of this 


---

### Reply from ~tiller-tolbus on 2024-07-10 22:08:02

A node can only send data to its children and its dependencies. So in order for data to get sent to a path outside of a node's namespace, it must include that path in its dependencies. 


---

### Reply from ~hastuc-dibtux on 2024-07-10 21:48:37

`~sarlev-sarsen` rhats exactly what’s being described in the para after «the shrub itself »


---

### Reply from ~sarlev-sarsen on 2024-07-10 21:36:28

Is there a possibility here to implement owen barnes' vision of a security model:
apps running on my machine have access to all the data, it is just in sending it elsewhere that it needs to ask permission?


---

### Reply from ~tiller-tolbus on 2024-07-10 18:34:06

`~hanfel-dovned` is currently working on make wizards which is Sky's presumptive answer to the both software distribution and the security flow. 

When instantiating a node, going through the wizard and telling it what its dependencies are allowed to be preserves the full power of the user to use components as general-purpose tools and also fully understand the security implications of their actions. 


---

### Reply from ~wolref-podlex on 2024-07-10 17:34:23

nice


---

