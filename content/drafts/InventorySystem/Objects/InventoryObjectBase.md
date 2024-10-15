---
title: "Inventory Object Base"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
`UInventoryObjectBase` serves as an abstract base class for inventory items within the inventory system. This class inherits from `UObject` and implements the `IInventoryItemInterface`, providing a concrete foundation for the inventory item logic. It defines essential attributes like item name, description, icon, and stack size, allowing developers to create various types of inventory objects quickly while maintaining the flexibility to override functionality.

The class is also designed to be fully integrated with Unreal Engine's Blueprint system, supporting Blueprintable and EditInlineNew, making it easy for game designers to create and modify item properties through the editor.

## Key Features:
- Abstract Base Class: This class is abstract, meaning it cannot be instantiated directly. Instead, other classes should inherit from it.
- Implements Inventory Interface: Implements `IInventoryItemInterface`, providing the foundation for managing item stack size, name, description, and icons.
- Editable in Editor: Properties like `ItemName`, `ItemDescription`, `MaxStack`, and `ItemIcon` are editable through the editor for ease of use.
- Blueprint Integration: The class supports full Blueprint integration, allowing for easy modification and extension in Blueprints.
- Data Validation: Implements `IsDataValid` for validating item data in the editor, ensuring items are set up correctly during development.

The `UInventoryObjectBase` class simplifies the creation and management of inventory items, offering editable properties and a solid foundation for further customization in both C++ and Blueprints. This base class allows developers to focus on defining the unique aspects of each item while ensuring consistency in how items interact with the inventory system.

## Authoring

You can author a new object via the Editor like you would any other asset. This is similar to how you would create a Data Asset, as using this method to create new items will allow you to load the items as needed using soft object pointers.

![](https://imgur.com/JHD71QH.png)

Setting up the Item's basic information is really simple, and has built in validation. This means that any errors in how you setup the items will be caught as soon as you save the asset. 
{{% hint warning %}}
Most of the data will return warnings (Item Name, Description and Icon) but the only one that will return an error is the Max Stack Size. This is because the Inventory Component requires 
a Max Stack Size of greater than 0, otherwise undefined behaviour will occur. If you somehow manage to bypass this, there is a built in `ensure` that will pick this up and prevent it from performing the
action. 
{{% /hint %}}

![](https://imgur.com/HdftmxJ.png)

## Inline Items

You can also create an instanced item object, this will create a completely unique item that can be passed into the Inventory Component. 

{{% hint warning %}}
Even if you put the exact same information into 2 different instanced items, they will be not be recognised as the same item. 
{{% /hint %}}

![](https://imgur.com/tOCgm6Y.png)

{{% hint info %}}
This is only a feature within C++, you cannot do this with purely Blueprint other than by using the functionality that already exists on the [Item Component]({{< ref "/drafts/InventorySystem/Components/ItemComponent" >}} "Item Component Documentation").
{{% /hint %}}


## Assigning to Actors

You can assign an Item Object Base using an [Item Component]({{< ref "/drafts/InventorySystem/Components/ItemComponent" >}} "Item Component Documentation") which is the quickest way to achieve this goal. If you already have an actor with an Interaction system that you have developed, then all you will need to do after adding an Item Component is pass in the Object. You can retrieve this with the following function:

![](https://imgur.com/reO1Ppo.png)

This function will automatically retrieve the correct item depending on if it is an authored object or an instanced object. This will depend on your settings on that [Item Component]({{< ref "/drafts/InventorySystem/Components/ItemComponent" >}} "Item Component Documentation").