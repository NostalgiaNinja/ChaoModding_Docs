# Tips for beginners: Texturing

Texturing your model brings your model to life with color. Blender's Texture Painting tools have a steep difficulty curve and sometimes are not the best tools for the job. You have options to work around this, though.

## Tip 1: Set your external app

This will be used for the later steps, so I decided to make this one on its own.

Go to Edit -> Preferences -> File Paths -> Applications. Find your image editor file path and browse to it. Save your preferences.

## Tip 2: Edit Externally

You'll find this in the "Texture Paint" Workspace. Go to Image -> Edit Externally to open your external app with the texture. This will open your editor of choice and bring the texture file into it. Press ++alt+r++ inside the texture area to reload the image once you're done.

## Tip 3: Quick Edit

Quick Edit is a handy tool to create a projection of your Blender scene to paint over it.  in the "Texture Edit" workspace, press ++n++ to bring up the properties panel on the right. Go to Tool -> Options -> External -> Quick Edit. 

Wait for it to take a screenshot of the object and place it inside your external application.  Make the changes as necessary and save the image. Close your external editor.

In Blender, click the "Apply" button to apply your quick edit.

## Tip 4: internal shortcut

If you really have to work internally in Blender, the following keys will be a lifesaver:

* ++f++ - Brush Size
* ++shift+f++ - Brush Opacity
* ++ctrl++ click - erase

Right clicking brings up a mini color picker that can be quickly used to change the swatch.

## Tip 5: Texture sizes

Make the texture sizes be equal to the power of 2 (2 x 2,  4 x 4,  8 x 8,  16 x 16,  32 x 32,  64 x 64,  128 x 128,  256 x 256,  516 x 516...).  This is for both the benefit of mipmapping and to avoid issues with the Texture Editor.

Also, if your texture is 1 solid color, make the size 4 x 4 pixels.  
It doesn't need to be huge; the 1 solid color will work the same regardless of size.  However, a smaller size will help avoid performance issues.
