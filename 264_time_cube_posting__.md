# time cube posting; 

**Author:** ~hastuc-dibtux  
**Date:** 2024-05-17 16:46:55  
**ID:** 170.141.184.506.806.456.414.556.070.271.741.067.264  
**Replies:** 2  

---

### Background

Clay, generally the most fleshed out vane in terms of its namespace has the type `$cass:clay` which is used to interrelate numeric cases with dates. However, clays versioning is on a per-desk basis, meaning that changing any file in a clay desk publishes new bindings for every file in the desk. 
This is something that shrubbery would obviously like to avoid, as it privileges desks as top level entities, which is something we don't have.


### Beginnings

To combat this, the first iteration of shrubbery had two different temporal dimensions, a version number for the data at the  node, and a version number for the whole tree at that node. This obviously maps closely to the %x and %z cares, so a third "child" version number was introduced.


### Timestamps

Obviously, to keep parity with clay, we should introduce a timestamp into the version number type, called an `$ever`


### Key handling

Given the proposed shrub key derivation system, we obviously need a mechanism to rekey individual shrubs, so we introduce a key number into the `$ever` as well, in addition to the ship's life


### Breaches

Urbit's inconsistency in breach handling has long been an issue, so let's fix that by putting the ship's rift into the $ever as well.


### Deletion

Shrubs may be deleted, and then reinstantiated. If the user desires to make a breaking change to the API of a shrub, it is required to delete and restart it. We treat this more or less as if the ship hosting the shrub had breached. (in fact, it's the reverse: we treat breaches as a special case of deleting the root shrub). We should  give each iteration of the shrub its own number, so that we can handle "shrub breaches". Let's stick the `shrub-rift` into the `$ever` as well.


### Shape numbers

In order to maintain good case discipline in virtual shrubs, we sometimes care about what the shape of the shrubbery tree is. Let's introduce `child-shape` and `descendant-shape` into the `$ever` which get incremented upon creation and deletion, but not on modification. Additionally, this has important use cases for merkelisation I do not understand. 
We have actually recapitulated our %x, %y, %z cases but for the shape of the tree, not the data inside it. This is true because `shrub-rift ` is basically `node-shape`



## Replies

### Reply from ~hastuc-dibtux on 2024-05-17 21:19:53

Libraries are not bound to the desk model at all 


---

### Reply from ~lagrev-nocfep on 2024-05-17 19:21:38

If you go down this road, then we can establish canonical versions of libraries and referent cores (e.g. on `%base`) without some of the duplication and maintenance issues we'll run into otherwise with desks.


---

