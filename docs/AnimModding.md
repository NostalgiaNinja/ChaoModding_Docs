# Custom Chao Animation

## Pre-requisites:

* Have completed the [Making a DLL Project](MakingProject.md) section
* version 4.2 of [Blender](https://www.blender.org/)
    * [Blender SAIO plugin v2.2.0](https://github.com/X-Hax/SonicAdventureBlenderIO)
* Animation theory
* Basic C++ Programming skills
* SA Tools (Make sure you've created an SA Tools Project!)
* Chao World Extended (Versions > 9.5)
* Patience

## What is a "Chao Animation"?

!!! note "A note:"
    CWE Animations are currently very limited in scope, and may expand in the future when interest and understanding of the Chao animation system grows. Currently, only **replacing animations** are supported, and new animations/behaviours may be planned/supported in the future.

Custom Animations are a part of Chao World Extended Chao API, where you can make your Chao move in a unique way.  Chao can be animated for a certain amount of frames, transitioned in and out of different animations, with different start and end frames, at different speeds. Chao World Extended introduced custom animations API support from version 9.5, but code has existed for it when the Omochao building features were added.

## Before we start:

* Make sure SAIO is up to date! As of writing, SAIO 2.1.5 is the most recent. Keeping SAIO and Blender up-to-date will help anyone helping you eliminate issues.
* Make sure SAIO is enabled in the Addons menu! If not, go to Edit -> Preferences and go to the Addons menu to install/enable "Import-Export: Sonic Adventure I/O"
* If SAIO errors out on any operation, and it complains about .NET runtime, install the [Microsoft .NET Runtimes](https://dotnet.microsoft.com/en-us/download) as instructed by the [SAIO Documentation](https://x-hax.github.io/SonicAdventureBlenderIO/).

!!! warning "A warning":
    Animations MUST have one root bone, otherwise exports will error out!

## Importing the model:

In blender, bring up the properties panel by pressing ++n++, and navigate to the SAIO Tools tab, then click import model.

![the Properties panel](imgs/Blender-NPanel.png)

Navigate to your project folder that you created with SA Tools (Should be in Sonic Adventure 2's folder under "Projects"), navigate to `Chao/Models/AL_RootObject` and select a Chao. Make sure that it is a sa2mdl file. For this example we will be using al_nnn.sa2mdl 

How to find what type your file is: Use [the Reference page on what Chao filename you want.](RefChaoFiles.md)

Select the 000 object and go to SAIO Tools -> Utilities -> Armature from Objects. Press OK on the dialogue box to generate a new armature. Delete the imported Chao (the hierarchy starting with the 000 object) and let's begin!

![Armature from Objects](imgs/blender-ArmatureFromObjects.png)

## Animating:

!!! tip "Things to consider"
    Consider the start frame, end frame and the speed of how your animation will look.  On Export, your animation will be set to "linear" interpolation and then keyframed on each tween.

!!! danger "be careful!"
    CWE Animations only support position and rotation for Chao! If you accidentally keyframe a scale component, follow [this troubleshooting step]() on how to remove an animation keyframe separately.

If you'd like, change the animation workflow to the "Dope Sheet" workflow, and then select the subworkflow as "Action Editor". This will allow you to see multiple (or all) keyframes at once and edit your keyframes if you're having trouble with viewing only one set of keyframes.

Select your Armature, so into Pose mode using ++ctrl+tab++ and select a body part.  Keyframe the starting frame for your animation, and press ++k++ to open the Keyframe menu. Select "Position", "Rotation" or "Position and Rotation" depending on what you've done.

Move the current frame playhead to the next frame you want to animate (you can skip frames if you'd like, exporting will interpolate the frames linearly) and make changes to the same body part. Keyframe the frame again and repeat as necessary.

Do this as many times as you'd like, for as many body parts as you like.  If you want to preview the animation, select all the keyframes, press ++t++ (interpolation mode) and select "Linear", then adjust the keyframes as you would like.

!!! note "Note:"
    Blender's animation framerate is 24FPS with a base of 1.000. This is **not** the same framerate that Sonic Adventure 2 plays Chao animations at.  It is currently unknown what the optimal framerate is for animating Chao at a 1:1 scale.


## Exporting the animation:

## Code:

## Creating the mod:

If you haven't followed [Making a Project](MakingProject.md), set up your mod folder. Copy the DLL file from inside your release folder into your mod folder and edit your "mod.ini" file to contain your DLLFile. For example:

```ini
DLLFile=ExampleMod.dll
```

Place your .saanim animations inside the mod folder.

Save your "mod.ini" file and test your mod!

## Troubleshooting:

If you have any issues with any of the mod creation process, check the [Troubleshooting page](troubleshooting.md) to see if your problem is mentioned. If you have other issues with the mod creation process, ask around in the Chao Island Discord. If the issue is of importance to note, it will be added to the documentation after being mentioned.