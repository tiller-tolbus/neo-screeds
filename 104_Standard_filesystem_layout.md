# Standard filesystem layout

**Author:** ~hastuc-dibtux  
**Date:** 2024-03-13 10:23:55  
**ID:** 170.141.184.506.702.435.591.701.645.121.346.863.104  
**Replies:** 0  

---

  /src - This is the "folder" for hoon source

    /std - This is the folder for "standard" marks/implementations (shipped as part of base distribution)

    * /imp - Implementations

    * /pro - Protocols

    /our - This is the folder for software hosted by the user

    * contains any number of folders /[desk], which contain  both /imp and /pro as per /std

    /ext - This is the folder for software that has been downloaded from elsewhere

    * Contains any number of folders /[ship]/[desk], which contain /imp and /pro as per /std

  * /reef - This is always present, and is the compiled stdlib (just `!>(..zuse)`)


