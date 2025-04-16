# Overlay namespaces

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-14 13:13:23  
**ID:** 170.141.184.506.753.624.714.871.120.829.186.310.144  
**Replies:** 0  

---

  `/moor`

    `/moor/conf/[term]/[implementation]`

    * This returns all shrubs that could be used to instantiate the dependency `term` for an shrub of type `implemenation`

    * case handling: simply the z care of `/`

    `/moor/able/[...path]`

    * This returns all the implementations that could possibly be written into `$path` 

    * case handling: sum of the case for `path`


### Sidebar on case handling

  Cases actually compose:

  * given a stateless overlay that is a join over {a,b,c} projections of the namespace then you can derive a synthetic case by simply adding the cases for a, b, c


