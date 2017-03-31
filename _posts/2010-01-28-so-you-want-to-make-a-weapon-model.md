---
title:  So, you want to make a weapon model
date:   2010-01-28
cover:  /media/header.png
excerpt: 'When creating the weapons, you have to adhere to a standard, or your programmer won’t like you very much.  I always visualized the bone that the weapon would be attached to at the origin, that way the programmer could shift every weapon the same amount and it would appear in the characters hands (it’s magic, trust me.)'
---
When creating the weapons, you have to adhere to a standard, or your programmer won’t like you very much.  I always visualized the bone that the weapon would be attached to at the origin, that way the programmer could shift every weapon the same amount and it would appear in the characters hands (it’s magic, trust me.)

I got bored of visualizing, and created the `AlignmentBox` models for this.  To create a shield, I opened `AlignmentBox_Shields` and made a shield that fit inside the box, and made it look good on the  character.  After finishing the model, I deleted the `AlignmentBox` extras and saved the model as the weapon – it would be perfectly scaled and rotated so that the programmer could work his magic to make it appear on the model.  The same thing applied to weapons, both main-hand and off-hand:  `AlignmentBox_Weapons` and `AlignmentBox_Weapons_Offhand` were used for these models.  The `AlignmentBox` models with bones were to place the correct bone at the origin.

So, to make a weapon model:

 - Open the appropriate `AlignmentBox` model
 - Create the weapon or shield model inside the box and so that it looks good on the character
 - Delete everything except your weapon or shield model
 - Save it!