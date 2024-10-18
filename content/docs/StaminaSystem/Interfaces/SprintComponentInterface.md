---
title: "Sprint Component Interface"
weight: 2
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


## Overview

The `ISprintComponentInterface` is an interface designed to be implemented by actors that utilise sprinting and stamina systems. It provides methods to access key components, such as `USprintComponent`, `UStaminaComponent`, and `UCharacterMovementComponent`. By implementing this interface, you ensure that any actor can interact with the sprint and stamina components in a modular and extensible manner, enabling flexible gameplay mechanics.

## Key Features

- **Modular Design**: This interface abstracts the access to key components, allowing different actors to share common sprint and stamina functionality.
- **Extensible**: Additional methods can be added without affecting existing implementations, making it easy to expand the interface with more capabilities.
- **Authority-only Methods**: Ensures that these methods are only accessible to the server, maintaining game logic integrity in a networked environment.
- **Blueprint Support**: Methods are exposed to Blueprints, providing the flexibility to implement or extend sprint functionality directly within the Unreal Engine editor.

---

## Functions

### Public Methods

---

```c++
USprintComponent* GetSprintComponent() const
```  
Category: Sprint  
**BlueprintNativeEvent, BlueprintAuthorityOnly, BlueprintCallable**

Description: Retrieves the `USprintComponent` associated with the object implementing this interface.

Returns:  
A pointer to the `USprintComponent` instance.

---

```c++
UStaminaComponent* GetStaminaComponent() const
```  
Category: Sprint  
**BlueprintNativeEvent, BlueprintAuthorityOnly, BlueprintCallable**

Description: Retrieves the `UStaminaComponent` associated with the object implementing this interface.

Returns:  
A pointer to the `UStaminaComponent` instance.

---

```c++
UCharacterMovementComponent* GetCharacterMovementComponent() const
```  
Category: Sprint  
**BlueprintNativeEvent, BlueprintAuthorityOnly, BlueprintCallable**

Description: Retrieves the `UCharacterMovementComponent` associated with the object implementing this interface.

Returns:  
A pointer to the `UCharacterMovementComponent` instance.

---
