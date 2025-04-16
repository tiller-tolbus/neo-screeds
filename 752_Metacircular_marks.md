# Metacircular marks

**Author:** ~hastuc-dibtux  
**Date:** 2024-02-22 12:38:55  
**ID:** 170.141.184.506.670.775.450.747.089.979.810.250.752  
**Replies:** 3  

---

Urbit is a series of bindings from names to noun and rules for having those bindings evolve. However, we do not want to have to rewrite code for each kind of noun that we wish to store. Hence we introduce the notion of a meta-noun. A meta-noun is a kind of noun that constrains a noun. 


## Typology

#### Prologue:

A `$name` is the canonical form of a name that binds a metanoun in the namespace


### Layer `.`: State

The simplest kind of metanoun is simply a binding from a `$name` to  a`$type`. Given a noun and a `$type`, we can validate it, we know what it is, and can pull faces from it to produce smaller nouns.


### Layer `+`: Convertible

A convertible metanoun is a binding from a name to 


```hoon
+$  conv
  $: =type
     grab=(list (pair name $-(vase vase))
     grow=(list (pair name $-(vase vase))
  ==
```

### Layer `+<`: Queryable

A queryable metanoun is a binding from a `$name` to


```hoon
+$  quer
  $:  =conv
      queries=(list $-([vase path] [name vase]))
  ==
```

This can be thought of as an inversion of a diffable convertible type, where the "state" is the path of the query and the "diff" is the noun. 


### Layer `-`: Diffable

A diffable metanoun is a binding from a `$name` to


```hoon
+$  duff
  [=type diff=name apply=$-([vase vase] vase)]
```

Here, apply


### Layer `->`: conformist

A conformist metanoun is a diffable metanoun whose diff is also convertible. Note that this is a more bounded version of rust's trait system. 


### Layer `-<`: mergeable

A mergeable metanoun is simply a diffable metanoun where the diff lists the `$name` of the metanoun as a potential conversion target (in `.grow`)  


### Layer `-<-`: reversible

A reversible metanoun is a mergeable metanoun equipped with an `.undo` gate, which satisfies the constraint that


```hoon
+$  rvrs
  [=duff undo=$-([vase vase] vase)]
++  example  (make-example type.duff.rvrs)
++  example-diff  (make-example (lookup-name diff.duff.rvrs))
++  contraint
  =/  new  (apply.duff.rvrs example example-diff)
  =/  old  (undo.rvrs new example-diff)
  ?>  =(old example)
  %.y
```

XX: Does a reversible metanoun really *need* to be mergeable? 


## Back to neo:

This typology of metanouns gives no concern to IO. This is quite deliberate, as it allows fairly seamless reuse of metanouns inside shrubs. For instance, importing a (diffable) metanoun with should allow one to just drop it into a shrub and just tinker with the IO.


### Service discovery

The external interface for a shrub is now


```hoon
:: nb: $pish is a pattern to a match a $pith
+$  shrub
  $:  pokes=(set name)
      :: possible metanouns for pokes
      casts=(set name)
      :: possible metanouns for the node
      query=(list [arg=pish ret=name])
      :: possible queries for the node
  ==
```


## Replies

### Reply from ~tiller-tolbus on 2024-02-28 16:36:14

Something like the pretty-path syntax in the Aegean blog post? 


---

### Reply from ~hastuc-dibtux on 2024-02-28 16:06:23

it should injective over FQSPs


---

### Reply from ~tiller-tolbus on 2024-02-28 14:42:01

Is a `$name` a FQSP? 


---

