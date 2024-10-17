# Setting up your development environment

## Visual Studio Project creation

!!! danger "Build types"
    Make sure you have installed "Desktop Development with C++" as UWP DLL Projects will not work for Sonic Adventure 2 mods.

1. Open Visual Studio (in the case of this guide, it will use 2022 Community edition)
2. Create a new project -> C++ -> Dynamic Link Library (DLL)
3. Name your project a suitable name, and place it somewhere easy to locate.  You will need to go to the folder to grab your DLL file once you've built it to create the mod.

![Create DLL](imgs/CreateDLL.png)

## Adding the dependencies:

Go into your Sonic Adventure 2 folder, and find the "programming" directory. Copy all of the files into your Visual Studio Project folder into your Visual Studio project directory. Note that your files will be read in the same directory as the Microsoft Visual Studio Solution file.

![Adding Dependencies](imgs/FileManagement_AddingDependencies.png)

For advanced users, the most up-to-date dependencies can be found in [Tools](resources.md) inside the "SA2Modloader includes" github page.

Clone or download `ModelInfo.h` and `ModelInfo.cpp` from [LibModUtils](https://github.com/X-Hax/sa2-mod-loader/tree/master/libmodutils).

To download the file in Github, click on each file you want, and click the download button on the right hand side of the header of the code preview.

![Github - Download Raw File](imgs/github-DownloadRawFile.png)

Place these two files into your Visual Studio Project folder, where the other dependencies have been placed.

You will need to change the first include in `ModelInfo.cpp` in order to fix a problem -- change `#include "stdafx.h"` to `#include "pch.h"`.

If you don't replace the include, this error will occur!

![Replacing an include](imgs/replaceinclude.png)

Afterwards, Add the files into your project by right clicking "Header Files" in your project explorer and going to Add -> Existing Item... to add `ModelInfo.h` and `ModelInfo.cpp`

![Add Existing Items](imgs/AddExistingFilesVS.png)

## Copying the boilerplate code:

Add a new source file and call it `main.cpp`

Copy the [Chao World Extended API Code Template](CWEAPICodeTemplate.md) and paste it into the fresh `main.cpp` file that you've added to the Visual Studio project.

## Getting the Chao World Extended API:

Get the [CWE API](https://github.com/cweteam/cwe_main/blob/main/cwe_api.h) from here! Download the `cwe_api.h` file and place it where you've placed all your includes.