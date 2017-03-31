---
title:  So, you want to texture your models
date:   2010-01-27
cover:  /media/header.png
excerpt: 'How to texture models, written by Erich!'
---
To texture models, select the item (or part of the item) you want to texture, and open the UV Mapper.  (Texture -> UV Mapper).   Most of the time, you’ll want a planar mapping, which is at (Mapping -> Planar -> Best Match).  You can select your own plane to create the mapping from (it’s like taking a picture from that angle).  You also might want to use cylindrical mapping for torsos and such – this is at (Mapping -> Cylindrical), and then whatever axis you want it to be cylindrical about.   I would recommend using User Defined axis and fooling around with the cylinder to make it look correct in the UV Mapper window.

The UV Mapper can look very messy with a lot of vertices in it, but if you hide parts of your model in the main screen, they won’t appear on the UV Mapper.

After you have made the UV Mapper look like you can see what you want to paint, hit (Edit -> Create Material with Outlines) to create the material.  Next, apply that material to your model (Texture -> Assign Material To Selection) and you’ll have lines appear on your model.  If you don’t see a lot of stretching or big square pixels, then you can go ahead and paint the texture.  I would recommend saving the texture as a file (Right click the texture -> Save texture as) and opening it in an alternative program like MS Paint or Photoshop.  Fragmotion’s 3d-painting software is useful for painting places on the model that you want to put onto your texture (such as locations of the eyes) but I didn’t find it that useful for a realistic-looking texture.  You can also download pre-made textures from the internet from sites that advertise free textures.  One good site I found was for Filter Forge, which can create many different textures for you and has a trial program.