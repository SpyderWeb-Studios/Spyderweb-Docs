---
title: "Inventory Item Interface"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

The `IInventoryItemInterface` is an interface that aims to aid in implementing inventory-related functionality in your game objects. This interface defines the key functions required for items to interact with the inventory system, such as adding, removing, using, and handling stack sizes. Developers can inherit from this interface to enable their game objects to work seamlessly within an inventory system.


## Inventory Methods

### `On Use`
This function will be called when an item is used. It should contain the core logic for what happens when the item is consumed or activated (e.g., healing the player, dealing damage, etc.).

### Utility Methods

#### `CanBeAddedToInventory`
Determines whether the item can be added to an inventory.
#### `CanBeRemovedFromInventory`
Checks if the item can be safely removed from the inventory. Override this method to provide conditions where removal is restricted, for example, when the item is quest-essential or bound to the player.
#### `CanBeUsed`
Checks if the item is usable. This method is essential for checking item usability based on context, such as whether the item is in the right condition to be used.

#### `GetMaxStackSize`
This function is vital for inventory management, especially when handling stackable items like potions or ammo. By default, it can return 1 for non-stackable items.

{{% hint warning %}}
This must return a value greater than 0, anything less than 1 will result in an `ensure` failing and the action you are attempting will fail
{{% /hint %}}

## UI Methods

### `GetItemName`
Retrieves the name of the inventory item. This function is critical for UI displays where the item’s name needs to be shown, such as in inventory slots, tooltips, or shop menus. The FText type ensures that the item’s name can be localized for different languages.
### `GetItemDescription`
Gets the description of the inventory item. This function should return a detailed description of the item, which might include gameplay information, lore, or usage instructions. The returned text can be used for tooltips, item inspection windows, or shop descriptions. Like the item name, the FText format supports localization for different languages.
### `GetItemIcon`
Returns the icon or image representing the inventory item. This function should return the 2D texture (icon) that visually represents the item in the inventory. Icons are essential for visually differentiating items in the player's inventory or store UI. Ensure that the texture returned is correctly set up in the content editor for display.

{{% hint warning %}}
This function return value will be updated/deprecated by returning a soft texture rather than a hard texture. This will be done to improve memory performance, please plan your code with this in mind
{{% /hint %}}