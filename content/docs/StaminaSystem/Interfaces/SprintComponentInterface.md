---
title: "Sprint Component Interface"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
# Sprint Component Interface

Unlike previous versions where the Stamina, Sprint and Character Movement components had to be on the same actor, we have updated the system to use an interface to be implemented on the owning actor of the Sprint Component. This is to allow it to successfully retrieve the relevant components, no matter where they are as long as the owning actor can reach them.  

If you choose not to implement this interface then the previous versions method will work, so this should be backwards compatible.

![](https://imgur.com/3xcmOko.png)

![](https://imgur.com/X3plYtD.png)

![](https://imgur.com/xtFxkU5.png)