---
title:  So, you want to make a character model
date:   2010-02-01
cover:  /media/header.png
excerpt: 'Load up `Default_Male_.ugh` into Fragmotion.  To create a human, use the Merge command (File -> Merge) and select `Default_Male_HumanHead.ugh` then hit “Open”.  Leave the settings as they are by default and hit “Ok”.  When merging files, I always do this unless otherwise specified...'
---
Load up `Default_Male_.ugh` into Fragmotion.  To create a human, use the Merge command (File -> Merge) and select `Default_Male_HumanHead.ugh` then hit “Open”.  Leave the settings as they are by default and hit “Ok”.  When merging files, I always do this unless otherwise specified.

Next, you want to weld the head to the body.  Use Weld All (Vertex -> Weld All) and set the Vertex Epsilon to 0.1.  This makes every vertex that is .1 or less units away from each other snap together and become one vertex.  Doing this should remove 14 vertices, and you’ll receive a notification in the bottom panel that 14 have been removed.

Now that the head is attached to the body, you want to smooth it all out.  Select everything (Edit -> Select All -> All).  Open the Model tab in the top-right corner of your screen, right click the Smoothing Group “All” and select the “Add Selection To Smoothing Group” option.  Now everything will be smoothed together.

Make sure to now deselect everything, otherwise you can seriously mess up the model.  I’m a bit paranoid (I’ve moved hidden bones by accident then gone on to work on the model, then had to start over and lost hours of work) so to do this I press and hold V (shortcut to select vertex), click on the background, press and hold G (shortcut to select group), click on the background, and then press and hold B (shortcut to select bone) and click on the background.   This action takes about a second or two and can save a lot of hassle in the future.

Now to texture the model.  Go into the Textures tab in the top-right hand corner, and click on the Body texture.   In the properties pane below it, click the “…” button in the Path box.  Navigate to and select `Default_Male_Human.bmp` and click “Open” (Note that this is a licensed image and so is obscured.)   Open the Boots texture the same way, and select “Default Boots.bmp”.

“Oh no!” You may say, “The body still isn’t textured!”  Don’t worry – I stored the textures on the head of the model, so now you just need to extend it to the body.  Select the torso of the character by pressing and holding G and then clicking the body (alternatively, you can go into the Model tab and right click the “Body” group and select the “Select Group” option).  Now you want to add the body texture to it, so assign the Body material to it (Texture -> Assign Material To Selection, click Body, and click “Ok”).  Now deselect everything, and you should have your human male.

Now would be a good time to save!  Make sure to use “Save As” so you don’t overwrite your base model – I used `Default_Male_Human.ugh` as my file name.

To create the Lucan model:

 - Open the `Default_Male_` model
 - Merge the Lucan head
 - Weld everything together
 - Smooth everything out
 - Apply the Lucan texture to the body and head
 - Apply the boots texture to the boots
 - Save the model!

Any head can be added to the base model this way – you can even make your own, as long as the vertices line up to the base model correctly.  You can also add the heads to different armor bases – try adding them to the Leather Armor base!