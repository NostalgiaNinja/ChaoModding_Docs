---
title: Chao World Modding Documentation
description: The current home for all things Chao Modding!
---
# Welcome to the Chao World Modding Documentation

Documentation version: 2.3.0

!!! tip "News!"
    Chao World Extended 9.6 has released with new API Code! View changelogs for more details and expect many changes if you're familiar with the older style of doing things.

This document serves to guide you through modding your Chao World, and is aimed at beginner modders looking to dip their feet into Sonic Adventure 2 Chao Modding.

This is a rehaul of the old modding documentation, which was initially only used for Chao World Extended modding. In future versions of this document, other mods will be included in the documentation. This is a working document and is always changing, so be sure to check back every so often for any nuggets of information that may be useful to you.

To get started, click one of the items in the list on the left of this section!


## Changelog:

* Version 2.3.0
    * Chao World Extended 9.6 now has a new API overhaul! Exant has provided many changes to the documentation!
        * Updated: Legacy Code notice for [checking if CWE exists](CheckCWE.md)
        * Updated: API Code references for new API
        * Updated: [Accessories](AccessoryModding.md) Documentation has an overhaul! use the New Chao World Extended Editor for accessory mods going forward, making the process much easier for modders to jump in and create their accessories!
        * Updated: CWE Team [Credits](credits.md)
        * Updated: Animation and Custom Chao Mods now require Versions >= 9.6
        * Updated: [Animation](AnimModding.md) Guide has new API functions, corrections and removed the transition section.
        * Updated: [Custom Chao](CharacterChaoModding.md) guide to refer to new API code.
        * Updated: New code API Code [examples](examples.md) have been created for the new documentation! Check the new Accessory, Animation and Custom Chao mod samples, along with the ID fetching code snippet.
        * Added: New Tool in [Resources](resources.md)! The Chao World Extended Editor now allows people to create Accessories with no code! Read up in the [Accessories Modding](AccessoryModding.md) guide!

* Version 2.2.0
    * Added: Animation Modding guide
    * Added: Reminder about troubleshooting page
    * Added: Info about contributing to the Chao Modding Documentation project
    * Updated: Troubleshooting page got reorganized into general and mod specific issues. Navigation sidebar can now be used to determine what mod you're troubleshooting
    * Updated: Accessory Guide now has mention of `AccessoryMakeBald()` and `AccessoryDisableJiggle()` functions
    * Updated: Mentions of "Armature from Objects" tucked inside Utilities menu.
    * Updated: Development Setup updated to use Github repository of SA2 Mod Loader.

* Version 2.1.2
    * Refactored: Moved generic project setup to the designated [Development Environment Setup](DevSetup.md) page.
    * Updated: SAIO and Blender version
    * Updated: Social Cards

* Version 2.1.1
    * Fixed: Clarification on versioning for SAIO and Blender
    * Updated the guide to the new mod loader method (the new hotness!)
    * Fixed: Lens documentation missing IDs
    * Added: Chao Palletes and Textures guide

* Version 2.1.0
    * Added: Character Chao using Custom Accessories.
    * Added: Character Chao Warning for changing positions.
    * Added: Nodes for horns in Animal Modding Reference Table.
    * Added: Troubleshooting for Black Market bugs.
    * Fixed: Custom Models in Lenses references Hats.
    * Fixed: Fruit doesn't have registerRare and registerCommon function calls.
    * Added: Warning about setting up projects, Don't use UWP DLL projects.
    * Added: feature to check if CWE is loaded

* Version 2.0.1
    * Fixed: Lens link not working (now added to the project code)
    * added further code examples in [Tools](resources.md) for users to peek into.
    * Added Changelog for historical purposes.

* Version 2.0
    * Initial Release of the new Chao World Modding Documentation.