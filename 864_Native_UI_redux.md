# Native UI redux

**Author:** ~hastuc-dibtux  
**Date:** 2024-02-27 15:28:48  
**ID:** 170.141.184.506.678.932.466.776.815.272.265.252.864  
**Replies:** 2  

---

### For reference, please examine the spec

[https://liam-fitzgerald.github.io/goon/](https://liam-fitzgerald.github.io/goon/)


### Argument

All user interfaces exist on a spectrum from "pixel-buffer-core" to "semantic tree". Pixel-buffer-core interfaces are dependent on the underlying input/output devices and are therefore not kelvin versionable. All semantic trees require a base layer of pixel-buffer-core.


### Input

Gathering and acting on user input in urbit fundamentally "bottoms out" at the creation of a poke. Ergo the platonic ideal of user interaction on urbit  is simply a partially filled out poke. Simply `form: context -> input -> poke`. 
An appropriate type for context would simply be the type of the current node being displayed in addition to the bowl. For an edit/delete operation on a node, this is the node itself. For an add operation, this is the parent node that the node is being added under.
So to define a form we have to define a schema for `input`, define the type of input and then write the function


```hoon
::  basically a mark but for UI
+$  scar  @tas
+$  schema
  $@  scar
  [p=schema q=schema]
++  todo
  |^  [id=@da title=@t remind=@da done=?]
  +$  diff
    $%  [%add todo=$]
        [%del id=@da]
    ==
  ++  sch
    [%cord %date]
  +$  sch-type  [@t @da]
  ++  form
    |=  con=[=bowl value=*]
    :-  sch
    |=  s=sch-type
    ^-  diff
    [%add now.bowl.con -.s +.s %.n]
  --
--
```

One could consider a button to be the trivial case where `input` is the empty type, with all of the context providing suffic


### TODO:

* this needs way more geometricity + space to put copy etc.

* disjoint subtypes



## Replies

### Reply from ~hastuc-dibtux on 2024-02-28 16:07:22

*monadic, I will not be taking further questions at this time


---

### Reply from ~hastuc-dibtux on 2024-02-28 16:07:04

Update: forms are nomadic


---

