# Care/case handling 

**Author:** ~hastuc-dibtux  
**Date:** 2024-03-18 13:10:33  
**ID:** 170.141.184.506.710.589.028.586.201.503.601.000.448  
**Replies:** 2  

---

## Names

* An `$ewer` is a `(pair stud cage)`

* A `$vial` is a `(pair stud *)`

* An `$ever` is a `[node=@ud tree=@ud]`

* A `$once` is a `$%([%node p=@ud] [%tree p=@ud])`

* A `$road` is a `[=name =ever grab=pith]`

* A `$name` is a `[=ship =pith]`

* A `$tour` is a `[=name =ever]`

* A `$pike` is an `(each road tour)`

* A `$bolt` is a `[=stud =once]`


## Supported cares

#### Data & children

* `%x` produces the state of the shrub -> `[=ewer =ever]`

* `%y` produces the state of the shrub with it's immediate children -> `(axil [=ewer =ever])`

* `%z` produces the state of the shrub with all it's descendants -> `(axil [=ewer =ever])`

* `%a` -> `%x`, `%b` -> `%y`, `%c` -> `%z`, except they are untyped


#### Metadata

* `%d` - Produces dependencies -> `(map term pike)`

* `%s` - Produces source shrub -> `$bolt`

* `%p` - Produces protocols supported -> `[read=(set bolt) write=(set bolt)]`



## Replies

### Reply from ~hastuc-dibtux on 2024-03-18 14:48:26

A stud is just a time varying reference to a mark. Arguably, all of these should be replaced with a `$bolt` which is a fully qualified mark reference. But this gets into the weeds of what the semantics of mark upgrades should be. i.e. should we require that mark upgrades nest in the previous type?


---

### Reply from ~rovnys-ricfer on 2024-03-18 14:45:30

what's a stud?


---

