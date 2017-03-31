---
title:  Problems recompiling Evidyon? Read about this editor bug!
date:   2010-04-10
cover:  /media/alphabanner2.png
excerpt: I talked with Eric this afternoon about his issues with his changes not showing up in the server after he recompiled the game. After looking over the code, I realized that when you hit "compile" I changed it so that the process of compiling and writing out the files occurs in a separate process...
---
I talked with Eric this afternoon about his issues with his changes not showing up in the server after he recompiled the game. After looking over the code, I realized that when you hit "compile" I changed it so that the process of compiling and writing out the files occurs in a separate process--this means that you have to wait a while before the changes are actually saved to disk! Rebuilding the game usually takes about 3-5 minutes. This can be fixed with some changes to the code, and has been added to the sourceforge tracker to be fixed at a later date.