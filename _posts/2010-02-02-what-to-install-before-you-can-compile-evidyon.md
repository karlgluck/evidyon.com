---
title:  What to Install Before you Can Compile Evidyon
date:   2010-02-02
cover:  /media/header.png
excerpt: Before you can compile Evidyon from source, you'll need the following things...
---

Before you can compile Evidyon from source, you'll need the following things:

1. Microsoft Visual Studio 2008.  A free copy of the Express Edition should work, but I haven't tested it.  Do this before any other step.
2. Microsoft DirectX SDK.  You need at least version 9.0c.  I used the August 2009 update.
3. Microsoft Platform SDK.  For VS2008 Professional this comes built-in; with the Express Edition I think you have to download the Windows Server 2003 R2 Platform SDK.
4. Download & unzip the Evidyon project files
Once you've installed all of this, all you should have to do is open "evidyon.sln" and hit F7 to compile the entire project.

If you start getting a bunch of errors about include files not being found or linker errors about missing libraries, the include/library file paths haven't been set up correctly in Visual Studio.  Add the "include" and "lib" directories for DirectX and the platform library to the appropriate sections in this dialog, under "Tools > Options":

![Include Files for VCPP Directories]({{ site.url }}/media/include-files-vcpp-directories.png)

Include Files directories in Visual C++ 2008
The first time, a complete rebuild of the project usually takes 15 to 20 minutes.  Once compiling finishes, run both the server and client by right-clicking on their project in the solution explorer, then selecting "Debug > Start New Instance".  The client usually takes a while (~30 seconds) to load when in debug mode.  After the programs start up, you will have a complete local copy of the game running on your machine.