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