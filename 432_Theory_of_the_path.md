# Theory of the path

**Author:** ~hastuc-dibtux  
**Date:** 2024-02-22 14:32:08  
**ID:** 170.141.184.506.670.900.759.685.622.371.746.578.432  
**Replies:** 6  

---

Looking through the previous attempts at shrub-likes, something that stands out is the uncertainty over what exactly a node should be, and what relationship it has with its children and ancestors. This is one of the primary difficulties with working on shrub-likes. 


### What is the namespace

The namespace (conceptually) is a `(map path noun)`. A namespace binding is the tuple `[=path noun=*]`. The noun is entirely unknown from the point of the namespace. So the only thing that gives our namespace structure is the path.


### Theory of the path

Given an arbitrary path `foo` in a namespace, we can derive a set `Ancestors` which is simply the set of paths who are prefixes of `foo`. Putting this to the side for now, we can also derive a set `Children` which is the set of paths for which `foo` is a prefix. 


#### Axiom 0

A metabinding is code that is designed to constrain the shape of a binding in the namespace. A metabinding constrains both the shape of the noun that the path is bound to, but also the shape of the metabindings permissible underneath it.


#### Axiom 1

A metabinding has a contract with its children. It looks and understands what is beneath its path, but does not (in general) assert anything other than what it is told about ancestor and cousin nodes. Almost a decade of webdev experience makes this axiom immediately obvious to me, and so will not be justified.


### Axiom 2

The conclusion of Axioms 0 and 1 is that a metabinding, when installed at a point in the namespace, defines a "zone of consistency" or a "transactionality boundary". Which is to say, the metabinding is responsible for defining an external interface with which it can be programmed. 


#### Axiom 3

We now need to separate the noun from its children. In practice, this means forbidding containers like `list, set, unit, mop` etc. from existing in the noun. These variable length containers should be legible inside the namespace. 
TODO: Finish



## Replies

### Reply from ~winter-paches on 2024-05-06 08:38:21

s what you meant?) I am saying, rather, that you could *add* information into the metabinding that would allow the addition of semantic information about the fact that this noun was intended to represent a variable length container.


---

### Reply from ~winter-paches on 2024-05-06 08:38:21

s what you meant?) I am saying, rather, that you could *add* information into the metabinding that would allow the addition of semantic information about the fact that this noun was intended to represent a variable length container.


---

### Reply from ~winter-paches on 2024-05-06 08:35:58

Hmm. I'm not sure I follow you. Although it is most likely that I just don't get the overall shrubbery "philosophy," being new to it. Anyway, the reason it is bad form to store a list in a tuple in an RDBMSes is because you have now introduced "out of band" information into the data model. (perhaps that'


---

### Reply from ~hastuc-dibtux on 2024-05-03 12:36:39

We "forbid" containers inside state, specifically variably sized containers (i.e. there is no upper bound on the size), for many of the same reasons that RDBMSs don't store lists in a column. The principle being that if you have a system of IDs, you want to avoid recapitulating that ID system at some other layer.


---

### Reply from ~winter-paches on 2024-05-03 12:17:17

I don't think that Axiom 3 should "forbid" containers like list, instead it should forbid "*mutable* containers like list." IOW, the metabinding of a list should include the cardinality of the defined noun and a pruner (shrub manipulator) who wants to alter the containers must instead make a copy.


---

### Reply from ~mastyr-bottec on 2024-02-28 04:37:31

Can you elaborate more on Axiom 3? Why is separation necessary? Would any shrub data (application data) requiring storage in a `list`, `set,` etc. simply need to be bound to a specific kind of path (say, for instance, `foo/resource/list`) ? Looking forward to the rest of this.


---

