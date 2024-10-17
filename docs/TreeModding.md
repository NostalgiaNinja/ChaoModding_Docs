# Tree Mods

## Pre-requisites:

* Have completed the [Making a DLL Project](MakingProject.md) section
* version 4.2 of [Blender](https://www.blender.org/)
    * [Blender SAIO plugin v2.2.0](https://github.com/X-Hax/SonicAdventureBlenderIO)
* Intermediate 3D Theory
* Basic C++ Programming skills
* SA Tools (Make sure you've created an SA Tools Project!)
* Chao World Extended (Versions > 9.5)
* An existing fruit mod.
* Patience

Tools can be downloaded [here](resources.md)

## What is a "Tree"?

Custom trees are an extension of the classic style of trees given to you by Sonic Adventure 2, where a Chao can dig up a patch of ground, place a seed, and watch the tree grow. Custom trees can grow garden fruit, or a custom fruit of your choice. Custom trees were introduced in Chao World Extended 9.5, alongside the API functions given to us.

## Modelling

### Before we start:

* Delete all default scene objects! These objects will crash your game if you do not delete them.
* Make sure SAIO is up to date! As of writing, SAIO 2.1.5 is the most recent. Keeping SAIO and Blender up-to-date will help anyone helping you eliminate issues.
* Make sure SAIO is enabled in the Addons menu! If not, go to Edit -> Preferences and go to the Addons menu to install/enable "Import-Export: Sonic Adventure I/O"
* If SAIO errors out on any operation, and it complains about .NET runtime, install the [Microsoft .NET Runtimes](https://dotnet.microsoft.com/en-us/download) as instructed by the [SAIO Documentation](https://x-hax.github.io/SonicAdventureBlenderIO/).


### Models you will need:

* A seed model
* A young tree/sapling
* An adult tree
* A dying tree
* Your already existing fruit mod.

Import the trees from `Chao/Trees` in your SA Tools Project Folder as a reference for the sizes of the default trees.

!!! danger "Heads up!" 
    Trees interpolate their data between their states, so all tree models ***MUST*** Have the exact same amount of vertices, otherwise your game will crash!

To assign a fruit location, create an [Empty](https://docs.blender.org/manual/en/latest/modeling/empties.html) (Plain Axes is recommended) object in the place you want it. You are allowed a maximum of 3 fruit locations.

!!! warning "a word of caution:"
    Vertex paint your model, otherwise your vertex interpolation will be glitchy and your final models will look strange and stretched. If you don't want to vertex paint your model, just enter and exit vertex paint mode on every mesh you create.

## Code

We will be using our fruit mod from a previous section.

In order to proceed, we will need a fruit mod. Take your existing fruit mod that you made from the [Fruit Modding Documentation](FruitModding.md) to get started. If you do not have a fruit mod. Make one by clicking the link to get started!

In the `main.cpp` file, inside the `extern "C"` function, define your seed and your trees as ModelInfo, like you did your fruit.

```cpp

ModelInfo* MDLExampleSeed;
ModelInfo* MDLSaplingExampleTree;
ModelInfo* MDLAdultExampleTree;
ModelInfo* MDLDeadExampleTree;
```

Create a Black Market Attributes for your seed.

```cpp
BlackMarketItemAttributes BMExampleSeed = { 500, 250, 0, -1, -1, 0 };
```

Inside the `CWELoad` function:

Create the `CWE_API_TREE_DATA` for your tree:

```cpp
		CWE_API_TREE_DATA ExampleTree =
		{
			MDLExampleSeed->getmodel(),
			MDLSaplingExampleTree->getmodel(),
			MDLAdultExampleTree->getmodel(),
			MDLDeadExampleTree->getmodel(),
			&texList_ExampleTree,
			"Exampletree",
			0,
			{ ExampleFruitID, ExampleFruitID, ExampleFruitID }
		};
```

Let's break this data structure down:

`CWE_API_TREE_DATA` - this is a struct which defines the tree inside of the CWE API which contains the following, in the following order:

* pSeedObj - Your seed model.

* pSaplingObj - Your young tree model.

* pAdultObj - Your fully grown (fruit bearing) tree.

* pDeadObj - Your dying tree model.

* pTexlist - Your texture list for the tree. Making this separate from the fruit is possible and recommended. Just use the same steps to create a custom texture file for this.

* ID - This is a text ID, Not used yet, but will potentially be used in the future.

* Flags - Unused - Keep at 0

* FruitIDs[3] - Here you can place multiple fruit on the tree, if you want to just use one fruit, just use the same fruit object three times.

Finally, Add the Chao seed by using the following code:

```cpp
cwe_api->AddChaoTree(ExampleTree, &BMExampleTree, "Example Seed", "Produces your fruit!");
```

### Building the Project:

Since your fruit mod was already set up, all you need to do is click on Build -> Build Solution, or press ++f6++.

## Creating the mod:

If you haven't followed [Making a Project](MakingProject.md), set up your mod folder. Copy the DLL file from inside your release folder into your mod folder and edit your "mod.ini" file to contain your DLLFile. For example:

```ini
DLLFile=ExampleMod.dll
```

Place your .SA2MDL models inside the mod folder.

Add a folder in your mod directory called "gd_PC", and inside that folder, add another directory called "PRS". Inside the "PRS" folder, add your `.PAK` texture files.

Save your "mod.ini" file and test your mod!

## Troubleshooting:

If you have any issues with any of the mod creation process, check the [Troubleshooting page](troubleshooting.md) to see if your problem is mentioned. If you have other issues with the mod creation process, ask around in the Chao Island Discord. If the issue is of importance to note, it will be added to the documentation after being mentioned.