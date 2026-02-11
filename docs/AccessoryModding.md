# Accessory Mods

## Pre-requisites:

* Have completed the [Making a DLL Project](MakingProject.md) section
* version 4.2 of [Blender](https://www.blender.org/)
    * [Blender SAIO plugin v2.2.0](https://github.com/X-Hax/SonicAdventureBlenderIO)
* Intermediate 3D Theory
* Basic C++ Programming skills
* SA Tools (Make sure you've created an SA Tools Project!)
* Chao World Extended (Versions > 9.5)
* Patience

Tools can be downloaded [here](resources.md)

## What is an "Accessory"?

Accessories are a part of Chao World Extended, and have been around since version 8.3 as part of a customization model. Intially intended to expand on the ideas of hats, but without removing the Chao's head. It eventually got expanded in version 8.5 with full-body accessories. There are two methods to creating an accessory, so it'll be a longer guide than usual.

## Before we start:

* Delete all default scene objects! These objects will crash your game if you do not delete them.
* Make sure SAIO is up to date! As of writing, SAIO 2.1.5 is the most recent. Keeping SAIO and Blender up-to-date will help anyone helping you eliminate issues.
* Make sure SAIO is enabled in the Addons menu! If not, go to Edit -> Preferences and go to the Addons menu to install/enable "Import-Export: Sonic Adventure I/O"
* If SAIO errors out on any operation, and it complains about .NET runtime, install the [Microsoft .NET Runtimes](https://dotnet.microsoft.com/en-us/download) as instructed by the [SAIO Documentation](https://x-hax.github.io/SonicAdventureBlenderIO/).

## Accessory Types:

As mentioned above, there are two types of accessories: Head accessories and Full Body Accessories. Both methods require different means of modelling so they will be gone into detail separately. The difference between head accessories and full body accessories are that head accessories work much like hats, but don't remove the head, and full body accessories allow you to rig your Chao to have the accessory follow them around.

## Modelling

### Importing the model

In blender, bring up the properties panel by pressing ++n++, and navigate to the SAIO Tools tab, then click import model.

![the Properties panel](imgs/Blender-NPanel.png)

Navigate to your project folder that you created with SA Tools (Should be in Sonic Adventure 2's folder under "Projects"), navigate to `Chao/Models/AL_RootObject` and select a Chao. Make sure that it is a sa2mdl file. For this example we will be using al_ncn.sa2mdl 

How to find what type your file is: Use [the Reference page on what Chao filename you want.](RefChaoFiles.md)

### Head Accessories

Head accessories are similar to hats, so the process is pretty much the same.

For head accessories, model or import your model where you want to place the accessory to be placed, minding the position of the head. Once your model is placed on the correct place, Add an Object Constraint, with the constraint being "Child of", and use the eyedropper on the head of your Chao.  Once done, click the "Clear Inverse" button to clear the Inverse Correction of the Child Constraint, putting it in place where it's supposed to be. On export, it will auto triangulate.

![clear inverse](imgs/modelling-set_inverse.png)

Note: There is a **vertex limit of 32768** per model.

Once done, delete the hierarchy of the Imported Chao.

![Save as SA2MDL](imgs/saveas_sa2mdl.png)


!!! info "A Warning about 'clearing inverse'"
    Clicking on "clear inverse" after contraining accessories might cause them to move around.

#### How to move the Accessories back to its original place after adding Constraints

First, before anything, make sure to apply all transforms.  Press ++ctrl+a++ and select "All Transforms".

Hold down ++shift+s++, and press ++1++.  Then select the model, hold down ++shift+s++, and press ++7++.  If your accessory has multiple models/meshes, do this for each model/mesh.  This works because the Chao's origin (the orange dot) should be at the world's origin (0,0,0).

This isn't needed for Body Accessories, since they do not use constraints.

### Body Accessories

For body accessories, the process is much more involved, and would need you to generate an armature in order to rig the model. 

Before you begin, take your imported Chao and note the names of the body parts you will be adding vertex groups to. For example:

```
al_ncz:
001_object_00016D7C - stomach
003_object_000167CC - left arm
010_object_00015B4C - right arm
```

Adjust for whichever Chao type you use.

Select the 000 object and go to SAIO Tools -> Utilities -> Armature from Objects. Press OK on the dialogue box to generate a new armature. Delete the imported Chao (the hierarchy starting with the 000 object) and let's begin!

![Armature from Objects](imgs/blender-ArmatureFromObjects.png)

Model or import your models over the parts you want to cover -- this can be any amount of body parts, be it hands, stomach, legs, or even wings! For this example, I'll be doing 4 parts - two on the stomach, one on the left arm, one on the right arm.

Select each of your models that you have imported or modelled, and go to the "Data" panel in the properties sidebar, and create a new vertex group. Name the vertex group the same as the body part you want to bind it to. Do this for every model you are adding as an accessory.

![Vertex Grouping](imgs/blender-VertexGroups.png)

Select your items to bind to the body, select the bone that corresponds to the name of the object (make sure that the bone selected has a rounded square surrounding it) and press ++ctrl+p++ to parent the bone (Do not use bone relative). go into pose mode (++ctrl+tab++) to test if the bone controls the accessory as well as the body part.

If your bone controls the accessory as you like it, there is no need for the next step. If not, do the following:

!!! tip "How to select bones"
    Select the Armature object, go into pose mode, and then select the bone you want to use.  Once selected, go back into object mode.

Weight paint your model by selecting your model (go out of pose mode by pressing ++ctrl+tab++ again), press A (to select all the faces), and go to the "Data" panel of your model you want to weight paint. A new section should appear where we defined the vertex groups. make sure the "Weight" slider is at 1.000 and click "Assign". This should make all the faces follow the bone we created. Tab out of Edit mode and follow the next step.


Delete all the "attach_" meshes that were created with the "Armature from Objects" process, and you're done! You now have a functional body accessory!

Note: There is a **vertex limit of 32768** per model.

![Save as SA2MDL](imgs/saveas_sa2mdl.png)

## Texturing in Blender

Texture your model as you would when making a model, taking into mind the size of your UVs. A smaller UV size would be preferred to make loading quicker.

Once done, open your texture menu in Blender, and open the SAIO Material Properties.

![Material Properties](imgs/texturing-Set_Texture.png)

Check the "Use Texture" checkbox to use textures for your model (1), and make sure to set your texture ID (2). this corresponds to the local ID that will be loaded when you look it up in Texture Editor. Do this for any other materials you're applying to the model.

Make to save and export your file as SA2MDL so that the texture information can be held by the file. You are now done with Blender and can safely close the file. Save a backup .blend file of your model just in case of complications or difficulties for someone to help out.

## Assigning the texture in Texture Editor

Once you're done with setting the above settings on Blender, save your model and your texture and go to Texture Editor.

![Texture Editor - Assigning the texture](imgs/TextureEditor-setting_textures.png)

Add or remove the textures you want in the mod by clicking the "Add..." or "Remove" buttons at the bottom of the window (1). The index (2) corresponds to the Texture ID that you set in Blender. Create a unique Global ID (3) for each of your textures, so that your mod doesn't conflict with other mods.

Save the texture file as `.PAK`, and keep it aside for later.

## Chao World Extended Editor

As of CWE 9.6 you no longer need code to add accessories. Download the [Chao World Extended Editor](https://github.com/Exant64/cweedit/releases/latest), extract the zip anywhere and run `cweedit.exe`.

### Mod folder structure

To use the editor your mod needs a `CWE` folder, and an `Accessories` folder inside the `CWE` folder. Your folder structure should look like
```
.                                                                                          
├── CWE
│   └── Accessories
│       └── some_test_model.sa2mdl
└── mod.ini
```

### Creating an accessory

You can create a new accessory file by clicking `File->New Accessory JSON`. Make sure to place your accessory JSON in the previously mentioned Accessories folder (the editor will not let you place it anywhere else).

You should now see the Accessory Edit view.
todo pic here

### 

## Troubleshooting:

If you have any issues with any of the mod creation process, check the [Troubleshooting page](troubleshooting.md) to see if your problem is mentioned. If you have other issues with the mod creation process, ask around in the Chao Island Discord. If the issue is of importance to note, it will be added to the documentation after being mentioned.


