---
title: "Sprint Component"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Sprint Component

This component holds the functionality for the sprinting, and has it's own stamina decay variables, and has the speeds built in so you can finetune the feel of the sprinting from the start. 

![](/assets/Stamina/assets/Examples/SprintComponentVariables.png)

`Server_ToggleSprintActive(bool bEnableSprint)` is the main RPC that you'll use to toggle the Sprinting on and off based on input. `ToggleSprint` is a Authority Only function so if you are already running logic on the server, then you can call this function without needing a new RPC. 

![](/assets/Stamina/assets/Examples/SprintComponentList.png)


