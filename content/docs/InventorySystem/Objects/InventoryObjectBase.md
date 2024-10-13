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

You can author a new object via the Editor like you would any other asset. 