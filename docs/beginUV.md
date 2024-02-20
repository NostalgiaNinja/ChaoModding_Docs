# Tips for beginners: UV Unwrapping

UV Unwrapping is a difficult subject, but it doesn't have to be teeth-pulling all the time. Most of the times, if your model is simple enough, you can get away with cheating the UV system and keeping certain UV islands around for details.

A useful tutorial to learning how to UV Unwrap from an environmental modeller is [here](https://twitter.com/Zhyrafaa/status/1708484934925455630)!

## Blender plugins recommended (but not needed here):

* [TexTools](https://github.com/franMarz/TexTools-Blender)
* [UV Packer](https://www.uv-packer.com/)

## Tip 1: Smart UV Project

Blender has a neat tool inside of it called "Smart UV Project." To access it, go to the "UV Editing" Workspace (it will automatically put you into Edit Mode), select the faces you wish to UV unwrap with the tool and press ++u++. The UV Unwrapping menu should appear. Click "Smart UV Project"

There's a few things we can tweak here:

* Angle Limit - The limit of which the UV will create a new UV island.
* Island Margin - How far from the edge of your texture map you'd like your UV islands to appear.
* Area Weight - How large the UV islands will be.

## Tip 2: Scale by 0

You can cheat a little if you just want a single main color by scaling by 0. Select a UV island, press ++s++ and then hit the 0 key. This will scale everything into a single point which you can use to color your objects as a single color. This allows the texture size to be really small (as small as sizes as 1x1), but effective for simpler projects where you only need solid colors.

## Tip 3: Export UV Layout

If you want to use your UV layout in an image editor to work on details, go to UV -> Export UV Layout. It will take the selected faces and export it into an image the size of your texture.

