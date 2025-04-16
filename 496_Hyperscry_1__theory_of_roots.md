# Hyperscry 1: theory of roots

**Author:** ~tondes-sitrym  
**Date:** 2024-05-20 02:56:30  
**ID:** 170.141.184.506.810.318.821.771.400.090.795.114.496  
**Replies:** 8  

---

*Root* is said (here) in two ways:


1. The namespace /, all that which is validly bound without prefix

2. The corollary 'superuser' with responsibility for permissions/capabilities and global names in that space (ex. Outside entities, known services, compiled builds)


Consider three sites at which / can be located, borrowing the // syntax from remote scry to denote it in a path:


  Ship: the complete local ([/~ship/]/) namespace

    ~tondes-sitrym//media or just /media is my root-level %media shrub, vs. /~tondes-sitrym/media, that shrub as named over the network

    * In general, any domain where we can drop the path prefix internally is the site of some kind of root

  * Contains/controls the permission, service, and build overlays applicable to all other shrubs on this ship

  * Concrete domain is at the discretion of the ship's operator

  Shrub: the local namespace according to a shrub embedded in it at some path + as laid out in hastuc's chroot screed

  * /foo/bar//baz: the root of /baz at /foo/bar/

  * By the axiom of relocatability, each shrub conceives itself as bound at / without awareness of intermediate lineage

  * So in the trivial implicit case, a shrubroot is just its normal interfaces, +kids and +band, and the permissions and name resolutions given at shiproot

    Nontrivial features are likewise lifted into ~ship// as an overlay, and might include:

    * Delegated permissioning of descendants

    * Alternate service bindings or build cache

    * Independent exterior identity eg. as a comet or moon

    * Introspection of its /parents lineage back to shiproot (in theory)

  World: the great global / in which all shrubs are conceptually bound, beneath their ship's identity, in accordance with the PKI, amen

  * ...and a global broadcast/scrybinding domain?

  * [mars:]//~zod

  * Domain is restricted to @p's, generally with discoverable networking keys ('Urbit IDs', 'Azimuth identities', 'ships')

  * Corresponding 'superuser' is a globally Byzantine fault tolerant (BFT) consensus - currently Azimuth/Ethereum, in a notional, unprincipled sense

    When we transition to a native self-hosted PKI, with BFT consensus run on network, then reprising our site structure so far it ought to be represented as a "network-level virtual overlay" of the ships whose global identity it guarantees, just as the root superuser at the intraship level comprises specialized overlays of local//space that define its global names and capabilities

    * This is the *hyperscry* namespace, and what it enables is a self-hosted metacircular identity system.

    * It includes everything under the worldroot that is not a single specific ship - consensus elements like blocks or mempool bindings, globally bound domains, anonymized or federated broadcasts...but I'm repeating myself.

    * It must therefore be virtual, in a sense to be fully developed, since every valid concrete message necessarily originates from some real Urbit identity. Or: hyperscry is still scry, not a transcendent, centralizing meta-level supplement to it. Anonymization, federation, global binding via or pursuant to consensus - all stand in some relation of overlay wrt material broadcasters.

    * It seems likely that the term *site*, so far used only informally, will be helpful to formally describe the 'dual of root' through which such data is present to us at each level.



## Replies

### Reply from ~tondes-sitrym on 2024-05-20 19:46:52

reprising dms with `~hastuc-dibtux`: by default we could populate `our.bowl` with a comet persisted until the shrub breaches that proxies to the host ship - shouldn't fuck up semantics unless hardcoding @p's or asserting on self ID type (planet/star..)


---

### Reply from ~hastuc-dibtux on 2024-05-20 10:26:25

`~tondes-sitrym`: Do you see a way to make this ergonomic, wrt. our.bowl ?


---

### Reply from ~tondes-sitrym on 2024-05-20 10:25:16

thanks guys - yeah it should be a capability rather than in the bowl imo. the most you should really need is your path up to an application root, if you're doing a layout-aware multiuse component sort of pattern. so the diagonal between bowl and ship-level permission could be creating a delegated/shrub root, and being able to truncate the location read


---

### Reply from ~hastuc-dibtux on 2024-05-20 09:51:08

But tbc, I suspect removing `here.bowl` is the principled thing to do, and is something I would like to do, if it does not limit our programming modeled


---

### Reply from ~hastuc-dibtux on 2024-05-20 09:50:19

The version of relocatability here is a pretty strong version of the original proposal. I'm not against removing `here.bowl` per se, just wondering whether you do actually need it. 


---

### Reply from ~tiller-tolbus on 2024-05-20 09:44:58

The existence of `here.bowl` is not really compatible with the axiom of relocatability. Devs can and will just parse `here.bowl` and ask their users to follow an install discipline that allows them to do so. I think `here.bowl` should be removed. 

Also bravo `~tondes-sitrym` 


---

### Reply from ~hastuc-dibtux on 2024-05-20 09:41:12

But the general structure of the argument here about `/` being the root shrub of consensus is good. 


---

### Reply from ~hastuc-dibtux on 2024-05-20 09:40:13

I support having a `home//` root as part of the standard distro, to separate things that could nuke your shit from trivial user programming (consider: `[%tomb /sys/ames]`.) Your point about the axiom of relocatability is interesting, because I wonder about the fact that one is not a root shrub being discoverable by checking `here.bowl` 


---

