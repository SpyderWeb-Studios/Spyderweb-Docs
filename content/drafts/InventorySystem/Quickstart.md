---
title: "Quickstart"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
bookCollapseSection: true
# bookComments: false
# bookSearchExclude: false
---

# Quickstart

On this page, we will go over how to get the plugin to work for your individual project, from the ground up

## Installation

You can either purchase the plugin from the Fab Marketplace, the Gumroad listing or from Github (access given to Patreons only). Alternatively, the plugin can be produced from the ground up by following our tutorial series on YouTube.

Download the plugin from your marketplace of choice and ensure that it is placed in the correct folder:

```
-| RootProjectFolder
--| Plugins
---| **InventoryPlugin**

```

{{% hint info %}}
**Use in Modules**

If you want to use any of the individual modules in your own C++ modules, simply add

```c++
PublicDependencyModuleNames.AddRange( new range [] {
"InventoryPlugin", "InventoryEditor"
});
```
to your build.cs files in your modules
{{% /hint %}}

## Setup