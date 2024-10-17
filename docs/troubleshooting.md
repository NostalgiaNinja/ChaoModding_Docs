# Troubleshooting

Below, are all the common issues that you'll have with your mods:

## Issue 1: Texture File Not Found

![Crash Dialog](imgs/SA2_Crash1.png)
![Crash Debug Console](imgs/SA2_Crash2.png)

Oh No! Your game has crashed! Something's wrong with your mod!

Not to worry! We have things that we can check!

A common crash would be that the texture file fails to load, and the game crashes. The following would usually resolve the issue:

* Check if your filename matches what you've written in code.

* Check if your TexList has enough space to load the texture file.

* DO NOT rename your texture file! Doing so causes the game to incorrectly find the file, and crashes the game. Instead, use the Save As option in TextureEditor, and make a new texture file with the name as given.

## Issue 2: Model File Not Found

![Black Market - Item Not Found](imgs/BlackMarket_Missing_Item.png)

Chao World Extended checks for the model, and if it doesn't load, will give you the above image. This can be a combination of things:

* The model can't be found in the location you specified. Place your model in the right directory and try again.

* Make sure your `pathStr` is pointing to the right place.  By default, the `pathStr` variable is as follows:

```cpp
std::string pathStr = std::string(path) + "\\";
```

This places it in the same place as where you put your `mod.ini` file.

## Issue 3: Character Chao - texture index is out of bounds

![Character Chao - Index out of bounds](imgs/CharacterChao_IndexOutOfBounds.png)

Chao World Extended checks your Character Chao model and it determines that your Texture Index is out of bounds. The following steps are required in order to fix it:

* Load your texture file into SAIO (If you don't know how to do so, click [here](https://x-hax.github.io/SonicAdventureBlenderIO/guides/texturing/#importing-exporting)!)

* Once your texture file is loaded, scroll down and look for the last texture in the list. Note down the number, and add 1 to that.

![Texture Count](imgs/TextureCount.png)

* Now that you've got the amount of textures, update your variable to the noted number.

![Texture Count - Variable](imgs/TextureCountVariable.png)

also, check the SAIO Material Properties on every object (including eyes, mouth and wings) and make sure that it is added to the texture file and inside the texture count.

![SAIO Material Properties](imgs/TextureCount-SAIO.png)

## Issue 4: Character Chao - Number of Nodes is not 40

![Character Chao - Number of nodes is not 40](imgs/CharacterChao-NumberOfNodes.png)

Chao World Extended checks your Character Chao model and it determines your model is not 40 nodes. The following steps are required in order to fix it:

In Blender:

* Turn on statistics in your Overlay Menu:

![Blender - Statistics](imgs/Blender-Statistics.png)

* Look at the total number of Objects. They should be 40, no more and no less!

![Blender - Total Number of Objects](imgs/Blender-TotalNoOfObjects.png)

* If you don't have 40 objects, you may not have joined your objects together, or you may have mistakenly joined your objects together. To join objects, press ++ctrl+j++ in Object Mode. to separate objects, press ++p++ in Edit Mode.

Note: If you accidentally joined objects from the Chao Model together, you will have to restart from importing the Chao model, as you have destroyed node data that is important for the Chao model to function.

## Issue 5: Character Chao - Wrong Chunk Type

![Character Chao - Wrong Chunk Type](imgs/CharacterChao-WrongChunkType.png)

Chao World Extended checks your Character Chao and determines that your model has an invalid vertex chunk type. The following steps are required in order to fix it:

In Blender:

* Go to the Data menu, and open the Color Attributes dropdown. If you see anything in here, remove it by clicking the - button.

![Blender - Color Attributes](imgs/Blender-RemoveColorAttributes.png)