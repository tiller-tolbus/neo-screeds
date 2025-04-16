#  it’s raining cats poms and pugs: or, the problems of transclusion

**Author:** ~hastuc-dibtux  
**Date:** 2024-05-02 09:14:41  
**ID:** 170.141.184.506.782.048.893.419.642.300.737.257.472  
**Replies:** 1  

---

### Definition

* "Synthetic data" - Data that is duplicated in the namespace. Specifically, if there exist two names A and B, with %x cares, which point to the same data, and have more or less the same provenance, but they are both being requested across the network and are in some way public, then the newer of A and B is considered "synthetic data"

* Non-example: A replication of a foreign chat in a local namespace, so that it can be annotated with unread counts and other client specific metadata, but is exclusively private, is ***not*** synthetic, because it's never being addressed over the network

* Example: A substack author importing a photo from another ship to display inside their blog post and, in doing so, rehosts the photo under a different name, ***is*** synthetic


### Why is synthetic data an issue

Much care has been taken in the layout of the layers of the namespace and the general design of shrub to maximize cacheability.
For instance, the difference between L3 and L4 namespace is precisely that L4 is synthetic data because in L4 a %y care is implicitly republishing the %x cares of it's children, whereas L3 avoids this problem (at the care layer anyway)
 However, the application model itself encourages too much synthetic data as a normal part of use. It's worth noting that early iterations of neo included something resembling a symlink, but this was ripped out in favor of just republishing the data, but this was short-sighted, as it introduces the synthetic data problem as outlined above, in addition to creating issues with the way signatures are managed and propagated.
So, it appears we must reintroduce symlinks. 


### Typology of shrubs

(with apologies to runtime devs, but apparently Ares retires this terminology)


* A "cat" - is a virtual shrub, conceptually `f(name, rest-of-namespace)`

* A "pug" is a real, "immediate" shrub i.e. just some data we bound ourselves.

* A "pom" is a real, "indirect" shrub i.e. just a name that says the data lives somewhere else. Poms, being delicate dogs, should be handled with care, and should never be pointed to as a dependency, or used in an overlay, or poked (just dereference it first). (TBD: why is this true). From the perspective of everything else (except scrying at L4), a pom is just a pug that contains a namespace reference. 



## Replies

### Reply from ~lagrev-nocfep on 2024-05-02 09:25:35

overloading our obscure terminology again


---

