# Shrub chroot and the path to full metacircularity

**Author:** ~hastuc-dibtux  
**Date:** 2024-05-02 08:40:55  
**ID:** 170.141.184.506.782.011.536.927.676.190.741.757.952  
**Replies:** 0  

---

This screed deals primarily with the (right now unclear) distinction between the "shrub runner" (app/neo.hoon) and the "root shrub" ( the thing that lives at /~ship/).


### Tasks that app/neo.hoon currently does (or is specified to do)

* Permission control on discovered dependencies

* Communicating with the outside (the fallen, non-shrub world)

* Service discovery

* Build system nonsense


The general idea behind a "shrub chroot" is that many of these can be lifted out and abstracted into an API that could live somewhere that isn't necessarily the root shrub. 


### Use Cases

This is idea comes out of conversations with `~tondes-sitrym`, specifically the notion of using service discovery to allow an AI agent to discover the kinds of tasks that it can do. Under the current model, this is immensely handicapped by the fact that when an agent tries to use one of these task descriptions (inject them as a dependency), it needs the user to explicitly intervene and grant these permissions. In general, it would be nice if we had an automatic AI supervisor for dependencies that are exclusively inside the AI shrub. We would still need permissions from the user if the AI would like to inject a dependency that escapes the AI shrub. 
Another possibility of the "shrub chroot" is making %aqua trivially easy to write. In fact it's arguable that the shrub port of %aqua is coterminous with defining an API for "root shrubs". 


### Compositionality of security 

Consider the path between any two shrubs A and B. You can draw the path between them by ascending to their most recent common ancestor from A and then descending to B. Any "root shrubs" passed through on the way must all agree to a dependency injection.


### Implications

Something that falls out of this quite interestingly is that the "root" shrub (at `/` ) is more or less equivalent to unix superuser. Then `/home` could be another "root shrub" that is equivalent to normal user permissions. 
Aqua could be run in a limited mode, where it just emulates the `/home` root, instead of the whole `/` root, using the necessary dependencies from the host ship. 
If you combine this with clandestine shrubs (the ability for a shrub to have signing keys that diverge from the usual hierarchy), then it's pretty clear to see how you could build a hosting product out of this.


### Next steps

The specific API that shrub chroots would have is TBD: it requires a heavy cleanup of the app/neo.hoon codebase in order to "see" what the root shrub/shrub runner distinction is. 




