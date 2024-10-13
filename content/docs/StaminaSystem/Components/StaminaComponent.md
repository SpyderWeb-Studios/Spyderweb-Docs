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

This is the main component that handles the system. It replicates the Stamina values to the clients and listen server.


These 2 functions are what you will be using in Blueprints to interact with the component on a basic level. 
```c++
/**
* @brief RPC to toggle stamina on the Server
 * @param bEnableStamina If the client is requesting the stamina to be enabled or disabled
 */
UFUNCTION(Server, Unreliable, BlueprintCallable, Category="Stamina|Toggle")
    void Server_ToggleStaminaActive(bool bEnableStamina);

/**
 * @brief Server Only Function to toggle stamina on the Server. Should be used over the RPC equivalent when possible.
 * @param bEnableStamina If the client is requesting the stamina to be enabled or disabled
 */
UFUNCTION(BlueprintAuthorityOnly, BlueprintCallable, Category="Stamina|Toggle")
    void ToggleStamina(bool bEnableStamina);
```

This is also where the Stamina Regenerate variables are stored, so you have a central place to balance these values. The function to regenerate the stamina is also blueprint callable so you can call it wherever you may need to. 

![](https://imgur.com/E6u9yeN.png)

Finally, the final major feature of this component is the ability to calculate if a certain action is viable with the amount of stamina left. This is support you to make your own components that communicate with the `Stamina Component`, such as for heavy attacks or other actions that require the usage of stamina

![](https://imgur.com/q3bcu1P.png)


Here is a list of all the available functions for this component

![](https://imgur.com/zUFfL9p.png)