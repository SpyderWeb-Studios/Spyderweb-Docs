---
title: "Quick Setup Guide"
weight: 1
bookFlatSection: true
bookToc: true
# bookHidden: false
bookCollapseSection: false
---

# Quick Setup

After installing, through the Epic Games Launcher or otherwise, let's walk through the steps to get started.

## Stamina Component

To add the Stamina functionality to an actor, simply add the [Stamina Component](/docs/StaminaSystem/Components/StaminaComponent) to the actor. If you want to replicate it, make sure that the actor itself is replicated. The component should be replicated by default. If you want some pre-defined functionality and BP access to the functions, then please add the `BP Stamina Component` instead.

{{% hint info %}}

If you want to use this for multiplayer, you need to ensure that the actor that you are attaching these components to are set to replicate 

![](https://imgur.com/ln4jd6a.png)

{{% /hint %}}

The sprinting is much of the same, just add the [Sprint Component](/docs/StaminaSystem/Components/SprintComponent) and make sure that it is replicating by default. Here is where you can set the decay rate and how fast you want the character to sprint. You also want to ensure that you have the [Sprint Component Interface](/docs/StaminaSystem/Interfaces/SprintComponentInterface) implemented on the actor, so you can define which [Stamina Component](/docs/StaminaSystem/Components/StaminaComponent) and Character Movement Comonent the [Sprint Component](/docs/StaminaSystem/Components/SprintComponent) should use. If you are using both on a character then you may not need to use the interface but it is still recommended.  

## Sprint Component

Similar to the [Stamina Component](/docs/StaminaSystem/Components/StaminaComponent), there is a BP version with easy access to the functions. It is recommended that you add the BP version rather than the C++ version, as the BP version overrides the `CanDecayStamina` function to prevent the stamina from decaying when the owning pawn is moving.

![](https://imgur.com/SnBWSVb.png)


From here, you should be able to bind any inputs to the `Server_ToggleSprintActive` RPC to allow your character to sprint.  


If you are having any issues with getting this setup, please have a look at the example character included in the plugin. 

![](https://imgur.com/DKNkUmF.png)

## Input

To actually trigger the Sprinting from the player controller, it is very easy. All you need to do is connect the toggle function to an input.

![](https://imgur.com/X8URLES.png)


## UI

We have provided a simple stamina widget with the plugin, which provides a nice and easy way to create a base for your own widgets.

![](https://imgur.com/apxuDop.png)

All you should need to do with this widget is add it to your own HUD and it will work out of the box. 