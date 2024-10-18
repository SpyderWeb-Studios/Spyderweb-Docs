---
title: "Stamina Widget"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

# Stamina Widget

## Overview

The `UStaminaWidget` class is a user interface element designed to display and manage stamina-related information for a character. This widget communicates with the `UStaminaComponent` to reflect changes in stamina values, allowing players to visualise their stamina status in real time. By leveraging Blueprint functionality, developers can easily customise the widget's appearance and behaviour within the Unreal Engine editor.

The widget that displays the stamina. Can be extended beyond the default widget.

It provides some basic functionality, such as listening to the stamina component for changes and updating the widget accordingly.

These are the only functions that come with the widget:

```c++

	UFUNCTION(BlueprintNativeEvent, Category="Stamina" )
		void OnStaminaValueChanged(float NewStaminaValue);

	UFUNCTION(BlueprintNativeEvent, Category="Stamina")
		void OnMaxStaminaValueChanged(float NewMaxStaminaValue);
	
	UFUNCTION(BlueprintPure, Category="Stamina")
		UStaminaComponent* GetStaminaComponent() const { return StaminaComponent.Get(); }

	UFUNCTION(BlueprintCallable, Category="Stamina")
		void SetStaminaComponent(UStaminaComponent* AttachedStaminaComponent);
```

You can use these to define the behavior of the widget when the stamina value changes.

By default the plugin will come with a widget that will update a progress bar with the new value, but 
you can extend the widget and override the functions to change the behavior.
## Key Features

- **Dynamic Stamina Updates**: Automatically updates the widget when stamina values change, ensuring the player always sees the most current information.
- **Blueprint Integration**: Provides native events and callable functions to be easily used and extended within Blueprints, enhancing user interface development.
- **Modular Design**: Allows for easy attachment to any actor with a `UStaminaComponent`, enabling flexible integration into various gameplay scenarios.

---

## Functions

### Protected Methods

---

```c++
void OnStaminaValueChanged(float NewStaminaValue)
```  
Category: Stamina  
**BlueprintNativeEvent**

Description: Event triggered when the stamina value changes, allowing the widget to update its display accordingly.

Parameters:  
`NewStaminaValue` – The updated stamina value for the character.

---

```c++
void OnMaxStaminaValueChanged(float NewMaxStaminaValue)
```  
Category: Stamina  
**BlueprintNativeEvent**

Description: Event triggered when the maximum stamina value changes, allowing the widget to update its display accordingly.

Parameters:  
`NewMaxStaminaValue` – The updated maximum stamina value for the character.

---

```c++
UStaminaComponent* GetStaminaComponent() const
```  
Category: Stamina  
**BlueprintPure**

Description: Retrieves the `UStaminaComponent` associated with this widget.

Returns:  
A pointer to the `UStaminaComponent` instance, or `nullptr` if not set.

---

```c++
void SetStaminaComponent(UStaminaComponent* AttachedStaminaComponent)
```  
Category: Stamina  
**BlueprintCallable**

Description: Sets the `UStaminaComponent` for this widget, enabling it to reflect the stamina information of the specified component.

Parameters:  
`AttachedStaminaComponent` – A pointer to the `UStaminaComponent` instance to attach to the widget.

---

### Private Members

---

```c++
TObjectPtr<UStaminaComponent> StaminaComponent
```  
Description: A weak pointer to the `UStaminaComponent` associated with this widget. This allows the widget to interact with the stamina system while ensuring proper memory management.

---