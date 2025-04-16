# Geology of the namespace

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-24 12:56:06  
**ID:** 170.141.184.506.769.543.595.323.680.879.651.323.904  
**Replies:** 0  

---

We stack our namespace in several layers


## L1 - Bootstrapping

The L1 namespace is simply 


```hoon
%+  map
  [ship rift life path case=@ud] 
[ever:neo (each vial:neo hash) oath]
```

This namespace is more or less the %x subset of the current namespace. 


## L2 - Perspectives

```hoon
%+  map
  [ship rift life care path case=@ud] [ever:neo (each vial:neo hash) life oath]
```

If `care` is not `%x` then the stud of the vial will be %tree (tba: better name) which is just an `(axal:neo ever:neo)` 
The `case` is required to match the `care`
Note that the L1 namespace is trivially embedded in the L2 namespace. It is just the subset of the namespace with an `%x` care.
Ames should use this level of the namespace in *responses*


## L3 - Tangled time

```hoon
%+  map
  [ship rift life care path case-index=@ud =once:neo] 
[ever:neo (each vial:neo hash) oath])
```

Here, we allow for addressing the namespace by anything other than the "canonical" case. For instance, say you're browsing a partially loaded axal and you have the %x case for some datum `/foo`, but would like to retrieve the %z perspective with the %x case that you have. Because it takes a $once as the temporal ID, you don't have to have the case match the care. Additionally we include a case-index to allow temporal identification anywhere in the path. If you have the case for some path `/foo` and you would like some path `/foo/bar/baz` then you would set the case index to 1. i.e. the "versioned" part of the path is `(scag case-index path)` and `(slag case-index path)` is your view inside that version.
Note that L2 is trivially embeddable inside L3, it's simply the subset of L3 where the `$once` matches the `$care` and `case-index` is `(lent path)` 
Ames should be able to handle requests for the L3 namespace, but should always respond with an L2 name


## L4 - Immutablity's last stand

```hoon
%+  map
  [ship rift life care path case-index=@ud =once:neo] 
[(axal [ever:neo (each vial:neo hash) oath]))
```

This is more or less the same as L3, however we realize children for %y and %z. This introduces a significant amount of duplication, making this level unsuitable for Ames to use. However, this is the most convenient layer for userspace to use referential transparency guarantees. 
Note that while L3 is not embedded in L4, there is a function f that allows to recover the L3 namespace (simply pull the root item out of the axal for %x cares and and drop the datums from the axal for %y and %z cares). 


## L5 -  Namespace of Theseus

Now we drop the referential transparency guarantees. The namespace maps a `[ship care path]` to a mutable `(axal [ever:neo (each vial:neo hash) oath])`
This is the level that most userspace shrubs should care about the namespace, leaving leveraging the power of referential transparency to the kernel. It allows userspace developers to treat shrubs as objects, which may change over time. This is also the only version of the namespace as yet implemented. 
We overlay L3 and L4 into the L5 namespace at `/layer/3/` and `/layer/4/` respectively. This allows, for instance, ford builds to be pinned to a case, letting developers opt-in to thinking more concretely about time.


## Addendum

It's notable that this stacking of namespace is what allows shrubbery to diagonalize the difference between immutable FP and mutable OOP.



