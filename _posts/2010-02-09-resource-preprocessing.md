---
title:  Resource Pre-processing
date:   2010-02-09
cover:  /media/header.png
excerpt: Describing every component of Evidyon's design is going to take a while, so I'm starting a series where I'll highlight major patterns that were the most useful during development...
---
Describing every component of Evidyon's design is going to take a while, so I'm starting a series where I'll highlight major patterns that were the most useful during development.

After the first few iterations of the game, I realized that the client and server would be significantly easier to write if they were given uniform input data that matched perfectly what was actually used at runtime.  The server's map would be big, flat arrays of structs that could be loaded straight from disk without any interpretation; the client could assume that all 3d models were in the format actually used to render the meshes.  This was the original inspiration for the game editor.  The purpose of the editor is to take a wide array of different media types, link them together, then compile them down into an optimized, consistent format.

This has several advantages:

1. The client and server can be faster and more simple when loading, since they can make more assumptions about the format of their data
2. It's easier to introduce support for new formats
3. The data can be optimized for their final purpose
4. Debugging and resource validation can be extensive without impacting end-user performance (because it's a compile-time operation)
5. Resources can be organized in any way you like during development because they're packed into a flat file for end use

Pre-processing resources was a big win for Evidyon and on a future resource-heavy project it would be one of the first things I would consider implementing.  However, in hind-sight I would have done things a bit differently on this project.

The editor really performs two phases that could be logically separated: converting resources to the uniform format and organizing them.  Both are preprocessing steps, but the former can be done before the editor is even started.  Having the editor perform the conversions from source format into the compiled format is a big source of the delay during compilation.  Most of the files don't change between versions, and having all that translation code inside the editor itself does make it more complex than it needs to be.  Plus, this would prevent something that always annoyed me: if the very last mesh fails to compile, you have to fix the problem then run the editor again from the start in order to see if it works.

If I were doing this again, I would write separate command-line utilities for each of the resource formats to do the translations.  One of these is already implemented--the animated mesh converter.  However, I'd like to have a utility for images, static meshes, maps, etc. plus a single "compile everything in all subdirectories" utility.  This would make it a snap to add new content--just drop in a new folder somewhere in the resources directory, run the compilation utility and check for any issues.

I guess the summary of all this would be, "preprocess as early and often as you can."  It's a lot easier to deal with well-formed, valid data right from the start.