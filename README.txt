# Fast Flipbook
A Houdini tool for speeding up reviews of viewport renders.
By Kieran Adams

# Description
Fast Flipbook aims to improve upon Houdini's default flipbook behaviour by simplifying the interface and exposing common parameters in addition to improving default behaviours through additional quality of life features for artists to use to improve their workflows. It syncs its settings with those existing in Houdini's native flipbook allowing artists to access additional advanced settings in a way they are familiar with and permits seamless switching from the default behaviour to the use of the tool.

The tool exposes frame range and resolution parameters to a simple, clear interface in addition to toggles for maximising the viewport, flipbooking all viewports, saving a .mp4 video of the resulting flipbook, and the option to export resulting videos to a chosen Discord Server through a webhook. When saved, outputs are stored in a '/flipbooks' directory of the $HIP file, their names being tied to the scene file name. The tool automatically versions up the file name to an index above the highest version number scene file in its parent directory to make it easy for artists to return to the state of their scene corresponding to the result of their saved videos.

Previous saved videos are retrieved from the '/flipbooks' directory upon loading the tool's interface and are displayed as a list in the tools integrated library. This library allows artists to quickly view their saved flipbooks through their system's default video player. The tool also provides functionality to compare an arbitrary amount of saved videos, compiling them into a grid with their filenames overlayed per image, saved with a unique name. These comparisons are also saved in the '/flipbooks' directory but are omitted from the library search, and will be opened if the user selects the same videos to compare - preventing unnecessary video generation.

A major aim of the tool was not requiring additional Python libraries, and so it leverages installed libraries from the Houdini installation for non-default Python libraries, including FFMPEG. The tool requires two supplementary files, its .ui file created with PyQt for its interface and a modifiable configuration file to store Discord webhook URLs with associated names, allowing for the removal and addition of webhooks through modification of a .json file which are recognised by the tool and its interface upon the next time it is used.

# Features
- Custom flipbooking interface
	- Exposed parameters for frequent settings
	- Non-exposed settings pulled from native interface preserving control
	- Additional quality of life toggles
	- Option to save mp4 and send to Discord

- Compilation of flipbook image sequences to video
	- Uses Houdini's FFMPEG install to compile images to mp4 video
	- Saves videos to $HIP directory
	- Ties video names to scene file names
	- Smart scene number versioning

- Saved video library
	- Displays videos from flipbook directory in $HIP
	- Option to open videos in system video viewer
	- Flipbook comparisons
		- Arbitrary number of inputs to grid
		- Resizing of inputs to fit HD grid structure
		- Labels added to help clarity of comparisons
		- Checks existing comparisons to avoid re-compilation
