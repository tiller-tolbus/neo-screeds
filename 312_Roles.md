# Roles

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-18 16:50:13  
**ID:** 170.141.184.506.760.239.911.331.572.694.816.653.312  
**Replies:** 3  

---

A `$role` is just another piece of "code", but this time in English.
It lives next to /pro and /imp in a folder called `/rol`. It contains an English language description of what it's semantics are. It is referred to by a `$stud`
Conversions may now be tagged with a role. Every conversion is automatically tagged with the empty role `%$` 
We now have a way of doing fairly primitive aspect-oriented programming. For instance, consider the role `%currency-receiver` we which we define as the following:


```plaintext
A conversion of role %currency-receiver is valid if the shrub is describing a transaction of monetary value. 

A conversion of type %currency-receiver should produce a type that describes the place where the transaction was sent.
```

We have now successfully prised semantics from the underlying representation. We could now change our `$port` type (which describes a set of constraints for dependencies and children) from: `[state=stud poke=stud]` to


```hoon
|%
+$  port
  $:  state=constraint
      pokes=(set stud)  :: this change should be done but is unrelated to the $role system currently under discussion
  ==
+$  constraint
  $%  [%and p=(list constraint)] :: union type
      [%or p=(list @tas constraint)] :: product type
      [%rol p=role q=constraint] :: decorate with role
      [%pro p=stud] :: base case
  ==
+$  wallet-event-constraint
  ^-  constraint
  :-  %or
  :~  :-  %eth
  
      :~  %and
          [%rol %receiver [%or [%ship pro/%ship [%addr pro/%eth-address] ~]]
          [%rol %sender [%or [%ship %pro %ship [%addr pro/%eth-address] ~]]
          [%rol %value pro/%wei]          
      ==
    ::
      :-  %sol
      :~  %and
          [%rol %receiver [%or [%ship pro/%ship [%addr pro/%sol-address] ~]]
          [%rol %sender [%or [%ship %pro %ship [%addr pro/%sol-address] ~]]
          [%rol %value pro/%microsol]  
      ==
  ==
++  wallet-event
  $%  [%eth receiver=pail sender=pail value=pail]
      [%sol receiver=pail sender=pail value=pail]
  ==

```

The rest of this screed is left as an exercise for the reader, however consider the implications of using the constraint system in specifying dependencies and children
TODO: how do roles compose? Do they relate to each other in any way? Does a role imply anything about the output of the conversion? can it constrain the conversion?




## Replies

### Reply from ~hastuc-dibtux on 2024-04-26 15:58:06

``[%not p=constraint]` 
should be a lawful constraint, along with
`[%only p=stud]` (prevent automatic conversions)


---

### Reply from ~hastuc-dibtux on 2024-04-26 15:57:48

Addendum


---

### Reply from ~migrev-dolseg on 2024-04-19 23:38:43

the render could check for a %docs role between <current-stud> and %htmx. if the developer defined the %docs conversion, the docs will get displayed in the "standard" documentation panel.


---

