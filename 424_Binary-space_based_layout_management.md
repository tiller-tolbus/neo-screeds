# Binary-space based layout management

**Author:** ~hastuc-dibtux  
**Date:** 2024-03-07 09:28:39  
**ID:** 170.141.184.506.692.878.044.330.852.136.647.655.424  
**Replies:** 0  

---

One of the central problems of native UI is resolving an abstract tree of data to a static component with sizing and so forth.
We first cut down our solution space by assuming a fixed rendering width at the top level. This is for the initial use case of a finder style view 
We have two cases to handle: 


* A node being rendered as a singleton

* A node being rendered as part of a homogenous collection 


The singleton node case is trivial, as there is an infinite amount of vertical space with which the node and its children can be rendered into. 
The homogenous collection case is a little tougher. We would like to display as much content as possible, whilst still maintaining homogeneity between rows. 
To achieve this, we tweak the meaning of the ordering of children in a heterogenous collection. We order heterogenous children in a `$goon` by their semantic importance, earlier being more important.
Then in order to find the row height, we walk the collection, sizing only the `%value` on the goon. We take the largest size that we find, then begin to lay that node out. We lay out the largest node by doubling the size of the `%value` to produce our entire bounding box. We then walk the tree breadth first, each item receiving half of the bounding box that is left, until we can no longer reasonably put items into the bounding box. We then take the structure of this layout and use it to paint the rest of the children.


