---
title:  Distributing Visual Studio Applications
date:   2010-02-06
cover:  /media/header.png
excerpt: One of the early frustrations I ran into with Evidyon was the dreaded "Application configuration incorrect" error that occurred when the game was run on some peoples' computers...
---
One of the early frustrations I ran into with Evidyon was the dreaded "Application configuration incorrect" error that occurred when the game was run on some peoples' computers.

From what I remember finding in a search for a solution, this is caused when a program built with Visual Studio is distributed on another computer without the correct SxS (side-by-side) dynamic link libraries.  Long story short, there's a direct way to solve this: make an installer program for your app.

It's annoying in that I actually would prefer an app that just ran without having to be installed, but I banged my head against this forever and it was the easiest way to solve the problem.  Once you make your installer app in Visual Studio, be sure to right-click on the project, pick  "Add > Merge Module" then select the .msm files for the CRT (C Run-Time) 9.0 and its corresponding policy.  It should look something like the following:

![MS Visual Studio CRT MSM](/media/ms-visual-studio-crt-msm.png)

Selecting the Visual Studio CRT Merge Modules to add to an installer project to prevent "Application Configuration Incorrect"

That's it.  Compile the installer for your app, then install the program on whatever computer wasn't working before.  Now when the program is run, it will have the correct versions of its libraries and the error won't come up anymore.

Afterthought:  I'm not sure if this is a problem when you statically link the CRT. I had problems with conflicting symbols when static linking Evidyon to the CRT early on in the project so I stuck with dynamic linking ever since.