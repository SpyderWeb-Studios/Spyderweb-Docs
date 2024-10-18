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

The USprintComponent is a modular and extensible component that handles sprinting functionality for a character. It interfaces with the StaminaComponent to manage stamina consumption during sprinting and is designed to work alongside the CharacterMovementComponent. This component manages sprint toggling, stamina decay, and speed adjustment during sprint and walk states.

## Key Features:
 - **Server-Side Sprint Toggling**: Handles sprint requests on the server with both RPC and local server functions.
 - **Stamina Integration**: Decays stamina when sprinting and stops sprinting when stamina is depleted.
 - **Customisable Sprint Behaviour**: Supports customisation of sprint speed, walk speed, stamina decay rate, and decay step.


![](https://imgur.com/QIoMQa9.png)

`Server_ToggleSprintActive(bool bEnableSprint)` is the main RPC that you'll use to toggle the Sprinting on and off based on input. `ToggleSprint` is a Authority Only function so if you are already running logic on the server, then you can call this function without needing a new RPC. 

![](https://imgur.com/Fu1bWRS.png)


## Extending the Sprint Component

Each of our components are designed to be extensible. With the Sprint Component the only function you can overwrite is the `CanDecayStamina` function, which controls at which point does the sprint component triggers the decay of the stamina. The BP version has this overwritten by default to prevent the sprint component from decaying stamina when the player character is not moving.

![](https://imgur.com/SnBWSVb.png)

## Functions

### Public Methods

 --- 
```c++ 
void Server_ToggleSprintActive(bool bEnableSprint)
```   
Category: Sprint | Toggle   
**BlueprintCallable**   
*Server, Unreliable*   

Description: RPC function to toggle sprinting state on the server, called by the client. This function is typically used to request enabling or disabling sprinting.

Parameters:   
`bEnableSprint` – A boolean value indicating whether to enable (true) or disable (false) sprinting.
 
 ---

```c++ 
void ToggleSprint(bool bEnableSprint)
```  
Category: Sprint | Toggle   
**BlueprintAuthorityOnly, BlueprintCallable**  

Description: Toggles the sprinting state on the server. This is a server-only function that should be preferred over the RPC variant when possible.

Parameters:   
`bEnableSprint` – A boolean value indicating whether to enable (true) or disable (false) sprinting.

 --- 

```c++ 
void StaminaEnabled(bool bArg)
```    
Description: Called when the StaminaComponent notifies this component that stamina has either run out or been restored.   
Parameters:   
`bArg` – A boolean value indicating whether stamina is available (true) or not (false).

 --- 

```c++ 
TWeakObjectPtr<UCharacterMovementComponent> GetCharacterMovementComponent() const
``` 
Description: Retrieves the CharacterMovementComponent that this component is attached to.   
Returns:  
A weak pointer to the UCharacterMovementComponent.
 
 --- 

```c++ 
TWeakObjectPtr<UStaminaComponent> GetStaminaComponent() const
```  
Description: Retrieves the StaminaComponent that this component is attached to.   
Returns:   
A weak pointer to the UStaminaComponent.

 --- 

### Protected Methods
 --- 

```c++ 
void SprintStaminaDecay()
```   
Category: Sprint | Base   
**BlueprintAuthorityOnly, BlueprintCallable**  

Description: Reduces stamina based on the StaminaDecayStep at intervals defined by StaminaDecayRate.

 --- 

```c++ 
void SetDecayVariables(const float& DecayRate, const float& DecayStep)
```
Category: Sprint | Base
**BlueprintAuthorityOnly, BlueprintCallable**

Description: Sets the stamina decay rate and decay step for this component.
Parameters:
`DecayRate` – The interval in seconds at which stamina will decay.
`DecayStep` – The amount of stamina to decrease per interval.

 --- 

## Members

### Public Members
 --- 

```c++ 
bool bSprintEnabled
```  
Category: Sprint | Base   
**Replicated, BlueprintReadOnly**  

Description: Boolean that indicates whether sprinting is currently enabled (true) or disabled (false).

 --- 

```c++ 
float SprintSpeed
```  
Category: Sprint | Base  
**EditAnywhere, BlueprintReadOnly**  

Description: The speed at which the character moves when sprinting. Defaults to 900.

 --- 

```c++ 
float WalkSpeed
```  
Category: Sprint | Base  
**EditAnywhere, BlueprintReadOnly**  

Description: The speed at which the character moves when walking. Defaults to 400.
 
 ---

```c++ 
float StaminaDecayRate
```  
Category: Sprint | Decay  
**EditDefaultsOnly, BlueprintReadOnly**   

Description: The rate (in seconds) at which stamina decays during sprinting. Defaults to 1 second.

 ---

```c++ 
float StaminaDecayStep
```   
Category: Sprint | Decay   
**EditDefaultsOnly, BlueprintReadOnly**   

Description: The amount of stamina that decays with each tick, as defined by StaminaDecayRate. Defaults to 1 unit.

 ---

### Private Properties   

```c++ 
TWeakObjectPtr<UCharacterMovementComponent> CharacterMovementComponent
```
A weak pointer to the CharacterMovementComponent this sprint component is attached to.

 ---

```c++ 
TWeakObjectPtr<UStaminaComponent> StaminaComponent
```
A weak pointer to the StaminaComponent responsible for managing the character’s stamina.

 --- 

```c++ 
FTimerDelegate StaminaDecayDelegate
```
A delegate used to manage the stamina decay function.

 --- 

```c++ 
FTimerHandle StaminaDecayHandle
```
A handle for the stamina decay timer, allowing control over the timer’s execution.
