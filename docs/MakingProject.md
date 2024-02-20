# Making a project

## Requirements
* Sonic Adventure 2
* Latest SA Tools

See [Tools](tools.md) to download these required tools if you haven't already.

## Setting up a mod folder:

1. Create a folder in the /Mods folder in Sonic Adventure 2
2. Create a new "mod.ini" file
3. Add the following text, entering the parameters required for the mod:

    ```
    Name=
    Author=
    Version=
    Description=
    GitHubRepo=
    GitHubAsset=
    UpdateUrl=
    DLLFile=
    Category=
    ```

## Creating a project

You should have your own SA2MDL files for Chao modification, as you will be constantly using them as references. This uses SA Tools to create a project structure that will rip the necessary models.

1. Open SAToolsHub.exe
2. Go to Projects -> New Project.
    * Select Sonic Adventure 2 for the game you are modding.
    * Select Template - PC - SA2
    * Click Create Project (The game should ask you where your Sonic Adventure 2 Folder is the first time around, that is where the game loads.) 
3. Let the game split all the project files as necessary. You should have a complete project with everything exported.