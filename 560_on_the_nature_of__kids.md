# on the nature of +kids

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-22 16:33:50  
**ID:** 170.141.184.506.766.596.975.445.060.526.601.666.560  
**Replies:** 0  

---

The +kids arm is woefully underspecified. The new behavior should be as such.


### "Capturing"

Capturing children means to provide a constraint for them. There are 3 different cases for capturing children. 


* The `%x` case: Do not capture children. Simple.

* The `%y` case: Capturing children non-recursively. This is the current behavior.

* The `%z` case: Capturing children recursively. This is slightly fraught, because it now allows two ancestors nodes to both constrain the types of their children. So we now need to implement a type algebra for children constraints, specifically the type intersection operator. (this is why this was not done in the original sketch).


### On capturing children recursively

If a child that captures with %x is beneath a parent that captures with %z, then  there may be a grandchild beneath the %x child. This grandchild is not visible to the child, but is visible to the parent. 
If a child that captures with %y is beneath a parent that captures with %z then we perform type intersection to ensure that both capturing mechanics do not produce the bottom type. The grandchildren are visible to both the parent and child, possibly with different perspectives. Great-grandchildren are not visible to the child, and are only constrained by the parent.
If a child that captures with %z is beneath a parent that captures with %z then we perform type intersection to ensure that both capturing mechanics do not produce the bottom type. All descendants are visible to both the parent and child, possibly with different perspectives.


### Interaction with the %gift system

The capturing also determines what %gifts go where. All ancestors that capture the child will receive %gifts. Because gift-giving is topologically ordered, the nearest parent will receive the gift with the change first. By the time further ancestors receive the gift, the gift may include the changes of closer ancestors also. 


### Addendum on dependencies

The +kids and +deps systems are now very similar. You can conceive of %gifts as a %rely but for +kids instead of %deps. With two large exceptions:


* Because gifts are inside the callstack, crashing on handling them will abort the tx

* Because deps can express constraints that are subsets of the constraints on the tree itself, any subpaths not matching the dep constraints are simply dropped. 


