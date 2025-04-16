# the metarely poke (please somebody help me with names) & metanamespace shenanigans;
or how I learned to stop worrying about breaches

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-22 17:02:02  
**ID:** 170.141.184.506.766.628.182.623.579.183.073.198.080  
**Replies:** 3  

---

Having dependencies means you can accept the %rely poke, and that will be automatically delivered to your shrub.
Now this introducing a question of what happens when your dependent shrub goes away or the foreign ship breaches (these are isomorphic operations in shrubbery, indeed each shrub keeps track of it's own `[=life =rift]` ) 


### Enter the metanamespace

The metanamespace is just a way to query for the current `rift` of a shrub. This will change whenever a shrub is tombstoned, or the ship breaches. It looks like


```hoon
/rift/[...path]
```

Every (non-frozen) dependency on some part of the namespace implicitly registers a dependency on the metanamespace. If you accept a %metarely poke (name should be updated) then when the shrub that you depend on breaches, you will be woken up with the %metarely poke. You may perform last-chance cleanup when handling the metarely poke, such as cancelling any pending request etc. If the dependency is marked as required, then if you do not attempt to update the (now-defunct) dependency, then your shrub will be suspended (rendered read only).
If you do not accept a %metarely, then the shrub will just be suspended.



## Replies

### Reply from ~hastuc-dibtux on 2024-04-22 17:10:07

ok that works


---

### Reply from ~tiller-tolbus on 2024-04-22 17:09:48

And the metanamespace should be called the Rift Namespace


---

### Reply from ~tiller-tolbus on 2024-04-22 17:09:30

I think the poke should just be called `%rift`


---

