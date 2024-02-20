# Fortune Teller Name Mods

## Pre-requisites:

* Have completed the [Making a DLL Project](MakingProject.md) section
* Basic C++ Programming Skills
* Chao World Extended (Versions > 9.5)
* Patience

## What is a "Fortune Teller Name"

The Fortune teller in the Chao Kindergarten can give random names to a player which can be customized by adding names to the preset and CWE names. CWE names can be 12 characters long, and is the easiest of the Chao World Extended mods to make. All you need is your DLL Project and your `mod.ini` file.

!!! note
    It is *recommended* to only use alphanumeric characters, as the fortune teller adding system does not support every type of character.

## Code:

### Adding the dependencies:

Go into your Sonic Adventure 2 folder, and find the "programming" directory. Copy all of the files into your Visual Studio Project folder.

![Adding Dependencies](imgs/FileManagement_AddingDependencies.png)

For advanced users, the most up-to-date dependencies can be found in [Tools](tools.md) inside the "SA2Modloader includes" github page.

### Copying the boilerplate code:

Add a new source file and call it `main.cpp`

Copy the [Chao World Extended API Code Template](CWEAPICodeTemplate.md) and paste it into the fresh `main.cpp` file that you've added to the Visual Studio project.

Above the CWELoad function, add a `char *` variable. For example:

```cpp
char TestName[12] = "testname";
```

Inside the CWELoad function, use the `cwe_api` API method and call the `RegisterFoName()` function. `RegisterFoName()` takes one argument: the `char *` variable you created just outside the function.

For example: 

```cpp
cwe_api->RegisterFoName(TestName);
```

### Building the Project:

Your solution configuration should be "Release" and your solution platform should be "x86" so that your mod is small, and does not have the additional code inside your mod. Your configurations should look like the following image below:

![configuration and platform](imgs/ConfigPlatform.png)

Build the project by pressing ++f6++ or going to Build -> Build Solution. If you have a "Build Succeeded" in your tooltip at the bottom left of your Visual Studio window, proceed. If you have a "Build Failed" message, have a look at the [Sample mod](examples.md) to see where you went wrong, and try again.

## Creating the mod:

If you haven't followed [Making a Project](MakingProject.md), set up your mod folder. Copy the DLL file from inside your release folder into your mod folder and edit your "mod.ini" file to contain your DLLFile. For example:

```ini
DLLFile=ExampleMod.dll
```

Save your "mod.ini" file and test your mod!

!!! warning "Disclaimer:"

    As there are a lot of custom names in Chao World Extended, it may take some time for your custom name to appear. 