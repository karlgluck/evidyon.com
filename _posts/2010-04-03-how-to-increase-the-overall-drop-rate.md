---
title:  How to Increase the Overall Drop Rate
date:   2010-04-03
cover:  /media/header.png
excerpt: To increase the drop rate for a given class of items (common/uncommon/rare) for all monsters using the editor, just double-click the "Treasure" line, right-click one of the % chances, hit "edit" and set a new value...
---
To increase the drop rate for a given class of items (common/uncommon/rare) for all monsters using the editor, just double-click the "Treasure" line, right-click one of the % chances, hit "edit" and set a new value. If you want to get an idea of what a given monster is dropping, go into the "Lifeform AI" entry, open up a monster, find its "Treasure" member, right-click that, then pick "View Drops". What comes up is a list of % chance to drop-vs-item.

Once you're happy, recompile the game.

To recompile the game, go to File > Compile... and select the existing files each for the ".evsvr" and ".evcli" files. This will overwrite them with your changes. Be sure to save the project somewhere in here as well!