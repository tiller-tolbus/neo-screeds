# Key handling

**Author:** ~hastuc-dibtux  
**Date:** 2024-04-02 12:40:11  
**ID:** 170.141.184.506.734.462.388.280.258.265.520.013.312  
**Replies:** 3  

---

## Purpose

to outline our system of keys in the namespace we should first outline what we would like to do with our keys. 


### Authentication

It would be nice if the provenance of a poke `src.bowl` was cryptographically verifiable.


### Permissions handling

We would like to extend the semantics of encrypted multiparty remote scry to shrubbery. Which is to say, private read requests should be gated by a key which can be rotated etc. Furthermore, unlike the current multiparty encrypted scry, we should have some notion of "inheriting" permissions from parent nodes. This allows, for instance, a chat and its messages to share the same key, allowing for one key exchange for the lifetime of the chat (barring rotations). 


## Sketch

Each shrub gets two version numbers to identify its keys


```hoon
|%
+$  pass  [rift=@ud life=@ud]
--
```

Yes, these have the same semantic meaning as when they are applied to ships. A change in the `rift` means discontinuity in the semantic meaning of a particular shrub. Changes to `rift` should trigger cleanup flows to anyone holding onto that state. A change in `life` just means a key rotation.
For authentication, we just need to hold onto a pub/priv key pair that is used to sign the provenance. For permissions handling, we need something slightly more complicated. 
Obviously the correct thing to do is something like BIP32, but with symmetric keys. But it's important that our key derivation function works with the namespace. So we need key derivations for each `$care` that we support (right now `%x`, `%y`and `%z` )


#### Properties of the key derivation functions for authentication/encryption:

##### Required

* CKD[x](parent_key_z, child_index) => child_key_x (this is more or less a hardened key pair in the BIP32 model)

  CKD[y](parent_key_z, child_index) => child_key_y

  * Such that CKD[x](child_key_y, grandchild_index) => grandchild_key_x

  CKD[z](parent_key_z, child_index) => child_key_z

  * Such that CKD[z](child_key_z, grandchild_index) => grandchild_key_z


(This is more or less non-hardened keys in the BIP32 model)
Note that BIP32 as constructed more or less satisfies the `%x` and `%z` cases, so maybe we can punt on `%y` ? 
A parent always has `%y` (possibly: `%z` ? undecided) permissions on its children, so we can always just give it the entire extended `%z` private key in its bowl so it can dole out permissions to it's children. 


### Write permissioning

TODO: Macaroons, privilege dropping, etc.
Can safely be punted on (you can always crash in `+poke` on any src.bowl) 




## Replies

### Reply from ~watter-parter on 2024-04-02 17:18:10

fwiw, macaroons do feel like a good fit for a model where you want shrubs to extend (a subset of) their own permissions to subshrubs. For example, shrub `foo` can pass `%y` permissions for itself (in the form a macaroon) to shrub `bar`, and `bar` can further restrict those permissions to a particular `%x` and pass them to shrub `baz`. When `baz` tries to read from `foo`, it includes the scoped macaroon, which `foo` can quickly verify. There's a good writeup on macaroons here: [https://fly.io/blog/macaroons-escalated-quickly/](https://fly.io/blog/macaroons-escalated-quickly/)

Of course, if you just need to control which apps can talk to other apps *within the same ship*, you don't need cryptography to enforce that. Maybe it's simpler to have cryptographic guarantees everywhere -- but that would be kind of a shame in terms of overhead.

The other thing I'd mention is that unguessable paths can serve as capabilities: that is, there's a model in which giving someone a path is equivalent to giving them permission to read the noun at that path (i.e. `%x`). To extend this to `%y`, you could give them a path that's bound to the list of children, and so on.


---

### Reply from ~hastuc-dibtux on 2024-04-02 16:46:26

retcon: I was quite feverish when I wrote this, it makes zero sense, please disregard


---

### Reply from ~rovnys-ricfer on 2024-04-02 13:53:43

`~watter-parter` curious what you think of these cryptographic requirements


---

