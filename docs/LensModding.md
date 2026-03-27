# Custom Lenses

## Pre-requisites:

* Have completed the [Making a DLL Project](MakingProject.md) section
* version 4.2 of [Blender](https://www.blender.org/)
    * [Blender SAIO plugin v2.2.0](https://github.com/X-Hax/SonicAdventureBlenderIO)
* Basic 3D Theory
* Basic C++ Programming skills
* SA Tools (Make sure you've created an SA Tools Project!)
* Chao World Extended (Versions > 9.5)
* Patience

Tools can be downloaded [here](resources.md)

!!! info "Credit"
    Massive credit to Erubbu who wrote the initial guide on Lenses, using the knowledge for the Anime Lenses mod. 

## What is a "Lens"

Lenses are a Chao World Extended addition, allowing you to change the texture of your Chao's eyes. They were introduced in Version 8 alongside the Custom Animal system, and are now available for customization and modification (>version 9.5)

## Modelling

!!! tip "Advice"
    Chao World Extended has a stock lens available. If you want to skip modelling a lens case, click [here](https://github.com/NostalgiaNinja/CWEAPI_ExampleLens/raw/main/lensNeut.sa2mdl) to download the stock lens!

### Before we start:

* Delete all default scene objects! These objects will crash your game if you do not delete them.
* Make sure SAIO is up to date! As of writing, SAIO 2.1.5 is the most recent. Keeping SAIO and Blender up-to-date will help anyone helping you eliminate issues.
* Make sure SAIO is enabled in the Addons menu! If not, go to Edit -> Preferences and go to the Addons menu to install/enable "Import-Export: Sonic Adventure I/O"
* If SAIO errors out on any operation, and it complains about .NET runtime, install the [Microsoft .NET Runtimes](https://dotnet.microsoft.com/en-us/download) as instructed by the [SAIO Documentation](https://x-hax.github.io/SonicAdventureBlenderIO/).

### Things you will need:

* A texture for the eyes (make sure they fit within the eye spec of a Chao model, test as appropriate)
* A model for your lens case.

## texturing

The following textures are needed in the following order:

* Default lens
* Small eyes
* Dark Chao eyes
* Hero Chao eyes
* Neutral Chaos Chao eyes
* Hero Chaos Chao eyes
* Dark Chaos Chao eyes

You're allowed to add any textures needed for the lens casing thereafter.

!!! note
    Hero and Dark swap around for Chaos Chao eyes. Bear this in mind.

## Code:

If you have not created a Visual Studio project yet, follow the instructions on "[Setting up your development environment](DevSetup.md)".

### Creating a custom Texture file:

Inside the `extern "C"` function, the following two lines:

```cpp
NJS_TEXNAME ExampleTex[10];
NJS_TEXLIST example_texlist = { arrayptrandlength(ExampleTex) };
```

Let's break these two lines down:

`NJS_TEXNAME` - The name of your texture loader. change `ExampleTex` with a unique name, and replace the number inside of the square brackets (the array assignment) to the amount of textures your mod will have.

`NJS_TEXLIST` - The texture list - Assign this to your `NJS_TEXNAME` so that it knows how to read it. Give it a unique name, since you reference this in any API calls that need your texture.

Inside the CWELoad function, Load the texture file with the following code:

```cpp
cwe_api->RegisterChaoTexlistLoad("ExampleTex", &example_texlist);
```

`RegisterChaoTexlistLoad()` takes two arguments - The name of your texture file (without the .PAK at the end of it) and a reference call to the `NJS_TEXLIST` that you created.

### Adding Black Market Attributes

Add the following code below the texture list variables:
```cpp
BlackMarketItemAttributes BMExampleLens = { 1000, 500, 0, -1, -1, 0 };
```

Let's break it down:

`BlackMarketItemAttributes` - This is a struct inside of the CWE API which contains the following, in the following order:
 
 * PurchasePrice - The selling price of the item sold.
 
 * SalePrice - the buying price if you're selling the item back to the Black Market.
 
 * RequiredEmblems - The amount of emblems required in the game (0 to 180 is possible in game, anything higher and they will not be able to be purchased through the Black Market.)
 
 * -1 - Name - Keep this as is, we define it in the AddLens function.
 
 * -1 - Description - Keep this as is, we define it in the AddLens function.
 
 * 0 - Unknown - Keep this as is.

### Adding Custom Models:

Create a `ModelInfo` pointer variable for each of the models you are about to add inside the `extern "C"` function. For example:

```cpp
ModelInfo* MDLExampleHat;
```

This is empty at the moment, so let's define it. In the `Init` function. underneath the `pathStr` variable, add the following for each model:

```cpp
MDLExampleLens = new ModelInfo(pathStr + "ExampleLens.sa2mdl");
```

Replace `MDLExampleLens` with whatever your `ModelInfo` pointer variable was called, and change the filename to the appropriate model.

### Adding the Lens

There's a few things we will need to add before a lens is able to be registered. In the `Extern "C"` function, add the following line just below the `RegisterDataFunc` function pointer:

```cpp
	//Lens function - Needed for CWE to recognize the lens.
	__declspec(dllexport) void(__cdecl* ALS_LensSpecial)(ObjectMaster*, ObjectMaster*);
```

After the line we just added, Generate an ID for each of the lenses you are making:

```cpp
    //Generate an ID for each lens
	int ExampleLensID;
```

In the `Init` function, add the following line just below the `PathStr` varaible:

```cpp
	//Lens function - This talks to CWE to get the lens to work when registering it as a special object.
	ALS_LensSpecial = (decltype(ALS_LensSpecial))GetProcAddress(GetModuleHandle(L"CWE"), "ALS_LensSpecial");
```

Now assign the lens ID to the `RegisterChaoSpecial()` function, to register it to the Black Market:

```cpp
    //Register your lens to the black market:
    ExampleLensID = cwe_api->RegisterChaoSpecial(MDLExampleLensBox->getmodel(), &Example_texlist, &BMExampleLens, ALS_LensSpecial, NULL, "Lens Name", "Lens Description", false);
```

And associate the lens with your texture:

```cpp
//Associate the lens as a custom eye color:
cwe_api->RegisterEyeColor("ExampleTextureName", &Example_texlist, ExampleLensID);
```

### Building the Project:

Your solution configuration should be "Release" and your solution platform should be "x86" so that your mod is small, and does not have the additional code inside your mod. Your configurations should look like the following image below:

![configuration and platform](imgs/ConfigPlatform.png)

Build the project by pressing ++f6++ or going to Build -> Build Solution. If you have a "Build Succeeded" in your tooltip at the bottom left of your Visual Studio window, proceed. If you have a "Build Failed" message, have a look at the [Sample mod](examples.md) to see where you went wrong, and try again. 

If you still can't get your build to work, try using the example mod as a template.

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
