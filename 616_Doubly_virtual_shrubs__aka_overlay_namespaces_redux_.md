# Doubly virtual shrubs (aka overlay namespaces redux)

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-24 11:10:10  
**ID:** 170.141.184.506.769.426.335.670.732.811.839.471.616  
**Replies:** 2  

---

A doubly virtual shrub is conceptually:


```plaintext
deps -> path args -> overlaid data -> overlay data
```

or, in hoon


```hoon
|%
::  +deps: Dependencies
::    same as in regular shrubs
:: 
++  deps  *deps:neo
::  +path: Initial part of path
::
::    Pattern match over start of path
::    i.e. if the doubly virtual shrub is bound at /foo 
::    then the overlay namespace will be
::      :(welp /foo path overlaid-path)
::    e.g. /foo/[arg1=@]/[arg2=@]/[...overlaid-path]
::
++  path  *(list aura)
::  +care: Perspective on the overlaid path
::    
::    required to maintain care discipline
::
++  care  *care:neo
::  +state: Type of the produced vase for +apply
::    XX: possibly should be 
++  state  *stud:neo
::   +apply: transform overlaid cane to overlay vase
::     .pith is only from the pattern in +path
::  
++  apply
  |=  [deps=(map term (pair pith cane:neo)) =pith =cane:neo]
  *vase
```


## Replies

### Reply from ~hastuc-dibtux on 2024-04-24 12:01:42

yes that's exactly the point


---

### Reply from ~tiller-tolbus on 2024-04-24 11:26:30

Can/should we use this to place `deps` at `/` and overlay namespaces like "all of the shrubs in my namespace such that they have UIs in HTMX"? 


---

