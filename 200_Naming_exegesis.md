# Naming exegesis

**Author:** ~hastuc-dibtux  
**Date:** 2024-05-07 16:56:13  
**ID:** 170.141.184.506.790.528.719.423.569.401.164.595.200  
**Replies:** 0  

---

```hoon
::  $hash: Hash
+$  hash   @uvH
::  $seal: Signature
::
+$  seal   @uvH
::  $myth: Binding, possibly tombstoned
::
+$  myth
  $:  pail=(pair stud (each vase hash))
      =aeon
  ==
::  $aeon: Sacred seal of time
::    Binding sans-data
+$  aeon  (pair ever seal)
::  $saga: Namespacing binding, not tombstoned
+$  saga
  $:  =pail
      =aeon
  ==
::  $epic: Binding w/ perspective
+$  epic  (axal saga)
:: +|  diffs
::  $mode: Kind of change
+$  mode  ?(%add %dif %del)
::  $yarn: Diff on binding
+$  yarn  (pair aeon mode)
::  $lore: diff over namespace (sans-data)
+$  lore
  (axal yarn)

```

### The proposed rectification

This does away with cane/wand/stem a & co, replacing them w/ $lore & $epic
Also paves way for actually using the geology of the namespace, and makes the upcoming networking rewrite easier


