---
title: "Stamina Component"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Stamina Component

The UStaminaComponent is a modular and extensible component designed to manage the stamina of a character. This component allows the character to perform stamina-based actions, such as sprinting, and it handles stamina regeneration and consumption. It also communicates with other components, such as USprintComponent, to manage stamina in relation to character movement.

## Key Features:
- **Stamina Management**: Tracks current and maximum stamina levels.
- **Action Validation**: Validates whether a character can perform actions based on stamina availability.
- **Stamina Regeneration and Consumption**: Customisable regeneration and consumption rates for different in-game actions.


## Functions

### Public Methods

---

```c++ 
float GetCurrentStamina() const
```  
Category: Stamina | Base  
**BlueprintPure**

Description: Retrieves the current stamina of the character.

Returns:  
The current stamina value.

---

```c++ 
float GetCurrentMaxStamina()
```  
Category: Stamina | Base  
**BlueprintPure**

Description: Retrieves the maximum stamina of the character.

Returns:  
The maximum stamina value.

---

```c++ 
bool CanPerformAction(float StaminaCost) const
```  
Category: Stamina | Base  
**BlueprintPure**

Description: Determines whether the character has enough stamina to perform an action based on the specified stamina cost.

Parameters:  
`StaminaCost` – The amount of stamina the action will consume.

Returns:  
`True` if the character can perform the action (i.e., stamina is sufficient), otherwise `False`.

---

```c++ 
void ToggleStamina(bool bEnableStamina)
```  
Category: Stamina | Base  
**BlueprintAuthorityOnly, BlueprintCallable**

Description: Toggles the stamina system on or off for the character.

Parameters:  
`bEnableStamina` – A boolean value to enable (`true`) or disable (`false`) stamina.

---

```c++ 
bool RegenerateStamina(float DeltaStamina)
```  
Category: Stamina | Base  
**BlueprintAuthorityOnly, BlueprintCallable**

Description: Regenerates the character's stamina by the specified amount.

Parameters:  
`DeltaStamina` – The amount of stamina to regenerate.

Returns:  
`True` if stamina has reached the maximum value, otherwise `False`.

---

```c++ 
bool ConsumeStamina(float DeltaStamina)
```  
Category: Stamina | Base  
**BlueprintAuthorityOnly, BlueprintCallable**

Description: Consumes the character's stamina by the specified amount.

Parameters:  
`DeltaStamina` – The amount of stamina to consume.

Returns:  
`True` if stamina has reached zero, otherwise `False`.

---

```c++ 
void OnRep_Stamina()
```  
**Description**: Replication handler for the stamina value, ensuring all clients are updated when stamina changes.

---

```c++ 
void OnRep_MaxStamina()
```  
**Description**: Replication handler for the maximum stamina value, ensuring all clients are updated when it changes.

---

```c++ 
void StaminaRegenerate()
```  
**Description**: Regenerates the stamina, typically called by a timer.

---

### Protected Methods

---

```c++ 
void SetRegenVariables(const float& RegenRate, const float& RegenStep)
```  
Category: Stamina | Base  
**BlueprintAuthorityOnly, BlueprintCallable**

Description: Sets the stamina regeneration rate and step size.

Parameters:  
`RegenRate` – The interval (in seconds) at which stamina regenerates.  
`RegenStep` – The amount of stamina regenerated per interval.

---

```c++ 
bool CanRegenerateStamina() const
```  
Category: Stamina | Base  
**BlueprintNativeEvent, BlueprintPure**

Description: Checks if stamina is eligible for regeneration.

Returns:  
`True` if stamina can regenerate, otherwise `False`.

---

```c++ 
bool CanConsumeStamina() const
```  
Category: Stamina | Base  
**BlueprintNativeEvent, BlueprintPure**

Description: Checks if stamina can be consumed.

Returns:  
`True` if stamina can be consumed, otherwise `False`.

---

```c++ 
void OnStaminaValueChanged()
```  
Category: Stamina | Base  
**BlueprintNativeEvent**

Description: Event triggered when the stamina value is changed.

---

```c++ 
void OnMaxStaminaValueChanged()
```  
Category: Stamina | Base  
**BlueprintNativeEvent**

Description: Event triggered when the maximum stamina value is changed.

---

### Protected Properties

---

```c++
bool bIsEnabled
```  
Category: Stamina | Base  
**BlueprintReadOnly, Replicated**

Description: Indicates whether stamina consumption is enabled for the character.

---

```c++
float Stamina
```  
Category: Stamina | Base  
**BlueprintReadOnly, EditDefaultsOnly, ReplicatedUsing=OnRep_Stamina**

Description: The current stamina value of the character.

Default Value:  
`100`

---

```c++
float MaxStamina
```  
Category: Stamina | Base  
**BlueprintReadOnly, EditDefaultsOnly, ReplicatedUsing=OnRep_MaxStamina**

Description: The maximum stamina value of the character.

Default Value:  
`100`

---

```c++
float StaminaRegenRate
```  
Category: Stamina | Base  
**BlueprintReadOnly, EditDefaultsOnly**

Description: The rate at which stamina regenerates when the character is not sprinting.

Default Value:  
`1`

---

```c++
float StaminaRegenStep
```  
Category: Stamina | Base  
**BlueprintReadOnly, EditDefaultsOnly**

Description: The amount of stamina that regenerates during each regeneration interval.

Default Value:  
`1`

---

### Private Members

---

```c++
FTimerDelegate StaminaRegenDelegate
```  
Description: Delegate responsible for handling the stamina regeneration process.

---

```c++
FTimerHandle StaminaRegenHandle
```  
Description: Timer handle used for managing stamina regeneration intervals.

---