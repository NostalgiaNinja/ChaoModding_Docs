# Setting up your development environment

## Visual Studio Project creation

!!! danger "Build types"
    Make sure you have installed "Desktop Development with C++" as UWP DLL Projects will not work for Sonic Adventure 2 mods.

1. Open Visual Studio (in the case of this guide, it will use 2022 Community edition)
2. Create a new project -> C++ -> Dynamic Link Library (DLL)
3. Name your project a suitable name, and place it somewhere easy to locate.  You will need to go to the folder to grab your DLL file once you've built it to create the mod.

![Create DLL](imgs/CreateDLL.png)

## Adding the dependencies:

!!! note "Changes to previous versions"
    SAModLoader no longer provides a "Programming" directory for modding the game. Download the SA2 Mod Loader repository and then copy the necessary files as needed.

Download the SA2 Mod Loader github repository [here](https://github.com/X-Hax/sa2-mod-loader/archive/refs/heads/master.zip) and extract it in an appropriate place.  For me, I usually keep a "libs" folder for all my libraries.

Once your repository zip folder is downloaded, go into `SA2ModLoader/Include`. Copy all the files here into your Visual Studio Project Directory.

Go back to the extracted zip folder, and go into `libmodutils`. There are a few files we interact with here:

|Type of Project|header file|CPP file|
|---------------|-----------|--------|
|Animation|AnimationFile.h|AnimationFile.cpp|
|Models|ModelInfo.h|ModelInfo.cpp|
|Levels|LandTableInfo.h|LandTableInfo.cpp|

Copy the relevant files you need (both the CPP and the header file) into your Visual Studio Project Directory.

With some files, they will fail to build with the following error:

![replace include file](imgs/replaceinclude.png)

If this happens to you, replace the `stdafx.h` include with `pch.h` and rebuild.

To add these files to your project, right click on a folder in your project explorer and go to Add -> Existing Item... and add the files you need (for example, `ModelInfo.h` in Header Files, `ModelInfo.cpp` in Source Files).

![Add Existing Files](imgs/AddExistingFilesVS.png)

## Copying the boilerplate code:

Add a new source file and call it `main.cpp`

Copy the [Chao World Extended API Code Template](CWEAPICodeTemplate.md) and paste it into the fresh `main.cpp` file that you've added to the Visual Studio project.

## Getting the Chao World Extended API:

Get the [CWE API](https://github.com/Exant64/CWE/blob/master/CWE/cwe_api.h) from here! Download the `cwe_api.h` file and place it where you've placed all your includes.