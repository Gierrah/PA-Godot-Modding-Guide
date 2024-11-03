# Creating custom maps for Pest Apocalypse
This guide is first to help you create your own maps for Pest Apocalypse, a game made in the Godot game engine. 
With help from the game's developers to encourage maps and modding, importing maps has been made incredibly easy.<br />
This guide is written with the goal to make it as simple as possible, for someone who's never even opened Godot before. (though experience with Godot, other game engines, or 3D software is recommended)

# Tools
To start, You're going to need:<br />
GDRE Tools (https://github.com/bruvzg/gdsdecomp) and Godot 4.3 .NET (https://godotengine.org/download/archive/4.3-stable/)<br /><br />
You're also going to need these Godot Addons<br />
DebugDraw 3 (https://godotengine.org/asset-library/asset/1766)<br />
Godot Jolt (https://godotengine.org/asset-library/asset/1918)<br />
Terrain3d (https://godotengine.org/asset-library/asset/3134)<br />
Protonscatter (https://godotengine.org/asset-library/asset/1866)<br />
<br />
Because much of Pest Apocalypse is written in C#, GDRE tools will not provide access to everything script related in the game. It also doesn't completely work for all the addons which is why we're downloading them separately. We are still able to work around these limitations, by movings scenes and assets into our own mod folder to edit them.<br />

# Preparing the Project
First, you're going to download GDRE tools, extract and run it. In the top left, click RE Tools > Recover Project.<br />
You're going to navigate to the folder containing your copy of Pest Apocalypse, and select the Pest_Apocalypse.pck file. Make sure that Full Recovery is selected in the options, and Select/Create a destination folder. You will want the project to have it's own folder. This is going to be where it decompiles the game, and where you'll do most of your file management. Click Extract. This may take some time as GDRE tools exports all of the project's resources. Once it's finished, it will generate a recovery report. You can click ok and close out of GDRE tools. You will not need it again.<br />

Inside this new folder with the decompiled game, we're going to create a folder called mods, and place the unzipped default_map folder that you've downloaded from this github inside that. It's important that you leave the name of the folder as it is for the moment. Anything you may want to add to your map in the game will be placed inside this folder (sub folders for organization can be used). <br />
Inside this folder, there is a mod.cfg file. Using this, you can change the name of your map, the description, and point to it's icon and map file. The map, icon, and terrain resources are all located here.<br /><br />
Inside the folder with the decompiled project, open the addons folder, and delete godot-jolt, terrain_3d, proton_scatter and debug_draw_3d. Now you're going to grab the godot addons from what you've downloaded before
Extract the zip files and find the addons folder. Inside the addons folder will be the addons that you want to copy, and paste into the addons folder for your decompiled Pest Apocalypse project.<br /><br />

# Editing your map
Now you're going to extract and open Godot 4.3 (Make sure you've got the .NET version. The exe will be called Godot_v4.3-stable_mono_win64.exe).<br />
You're going to click Import/Import Existing Project, and navigate to the folder you've been setting up with the decompiled project. Click Import & Edit. This may take some time.<br />
Once it's finished importing, you'll close out the editor. You don't need to save yet. Reopen Godot and the project. This will let the addons properly start, and let you use terrain3d in particular.<br /><br />

In the bottom left hand corner is the file manager, you can navigate through the mods/map_name folder and find the files you've downloaded.<br />
<img width="142" alt="windowsnip" src="https://github.com/user-attachments/assets/f465d1bb-a05d-48e3-9935-cb296f5d0f2c"><br />
You can double-click the map.tscn file to open it. From this point, you can also rename this folder to be the name of your map/mod. Changing this name should be among the first things you do, as Godot may be a bit finnicky if you want to add resources to your game later on. You should change the name from within the editor by right-clicking on the folder.<br /><br />

Map editing works by referencing all the existing scenes and assets already withing the game. If there's anything you want to add that isn't already in the game, you should store it within your map folder to ensure that the map can reference it correctly when running. You can copy and paste scenes from within the game's files to within your mod folder, and make any edits you'd like to those scenes from there. To import those edits, you would delete the node in your map, right click on it's parent node, and click "Instantiate Child Scene" to search for your edited tscn file and add it. 
You can edit terrain by navigating to the LevelGeometry>Terrain3D node.
You shouldn't touch anything under NecessaryNodes in the node tree. Nodes under LevelDesign are where you'll do most of your editing. You can copy, paste, and move nodes around to create your level. 

Remember to save often! Once you're done with your level, you can copy the mods folder from within the project, and paste it into your Pest Apocalypse game directory. 
