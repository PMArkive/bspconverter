# bspconverter
A Source Engine tool that converts BSP 21 maps into Source 2013 engine branch without decompilation.

# Installation
Grab latest release [here](https://github.com/PiMoNFeeD/bspconverter/releases) for either SDK 2013 SP or MP. Extract it to your SDK root folder (`bspconverter.exe` must live inside `bin` folder!)

# Usage
```
bspconverter [options] bspfile
```
Options:
```
-nolightdata          : Doesn't save any light information in the fixed file
-spewmissingassets    : Logs every missing brush texture and static prop model

-vproject <directory> : Override the VPROJECT environment variable
-game <directory>     : Same as -vproject
```

# Building
Building this is pretty straightforward if you didn't modify any compilers in your fork of Source SDK 2013:
- Merge `vpc_scripts\projects.vgc` and `vpc_scripts\groups.vgc` from this repository with your fork of Source SDK 2013.
- Replace `utils\common\bsplib.cpp` and `utils\common\bsplib.h` from your fork of Source SDK 2013 with files from this repository.
- Copy `utils\bspconverter` to your fork of Source SDK 2013.
- Build your code as normal.

If you *did* modify them, you'll have to merge changes from `utils\common\bsplib.cpp` and `utils\common\bsplib.h` manually with your code.

## Why isn't this tool standalone (independent of Source libraries)?
I figured it would be much simpler to expand on existing compilers' functionality of loading and writing BSP files, and it allows you to define your own lumps by just adding this tool to your engine branch, as opposed to having to edit all the headers and structures manually.
My plans are to make this tool fix up lumps based on datadescs, rather than manually fixing up each version by hand like it is now.