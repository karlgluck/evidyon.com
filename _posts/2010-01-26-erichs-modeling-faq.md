---
title:  Erich's Modeling F.A.Q.
date:   2010-01-26
cover:  /media/header.png
excerpt: "A whole bunch of questions about Evidyon's models and FragMOTION answered by Erich!"
---
# The models in the “##Complete ..” folder don’t have textures!

Yes they do, they’re just not duplicated to that folder.  If you want to texture them, look for the appropriate textures in the “##Item Sets” folder.  (Eg. Acidweave Doublet texture is in “##Item Sets\9 – Acid\Acidweave Doublet.bmp” and the Human, Lucan, Geonan, etc. textures are in the “##Item Sets\1 – Default\” folder.)

# Why are some of the textures in such bad quality?  Why do they look like cartoons?

We licensed the textures from a company and are bound by their license agreement.  We cannot distribute the textures in their raw format, so we are distributing images that look similar, but are obscured enough to not violate the license agreement.

# What is “Testerboxes.ugh”?

This model is meant to be merged with the base models to test the limits of the animation.  All of the weapons and shield are to fit within those boxes.  When creating the animations, I used these boxes on the character to make sure that weapons and shields would not clip through each other.

# What is “AnimationsModel.ugh”?

This model is a merge of the latest default male model and the testerboxes, all with the textures on them.  The different colored lines on the handles are for placement of the hands for different weapons (hide the LBlade and RBlade groups to get a better view of the handles) – you can see which colors correspond to which animations simply by going through the animations – it should be pretty obvious ;D

# Why is there a separate model for animations?

With one model for animations, they only need to be updated on that one model (the same animations are used for male and female models because they have the same bone structure) and when working on a model, the saving process is sped up because it doesn’t have to save the animations.   When the model needs to be tested for animations, I simply merge in the animations from the animations model and do the testing.



# Why isn’t the character model posed with straight arms and straight legs?

The short answer is for animating.  This character model is in a halfway-pose (a pose I picked up from a Google Book about 3d modeling.. I can’t find it now unfortunately), where everything is bent halfway between its two extremes.  Instead of having arms look their best when they’re pointed out straight, why not have them look their best when they’re near the sides of the character, where they will most often be?

# Why is there a bone at (0,0,0) called the “Origin” bone?

This bone helps when animating and graphics.  If you want to make the entire character rotate about the origin, it’s a lot easier to do if you have a bone there to rotate around.  For graphics, it gives another attachment point for decals and/or models.  In Evidyon, we wanted to create a transparent egg around the character for a shield spell – the egg model was attached to the origin bone so that the character could pivot and move freely without the egg model moving anywhere.

# What do the “RightWeapon”, “LeftWeapon”, and “LeftShield” bones do?  They’re not attached to anything!

They are not attached to anything in the base model.  When weapons are attached to the model, they use these bones.  If you merge the Testerboxes model into the Default_Male model, you will see that the weapons and shield are attached.

# Why do all the joints have 3 rings of vertices around them?

Joints are a pain that can’t be solved by arthritis medicine.  In animating, I found it easiest to have 3 rings of vertices at joints that were attached to separate bones on each side of the joint to provide a smooth look for joint rotation.

# Why are there so many bones?!

The more bones I had, the less vertex weight shenanigans I had to deal with.  The original model had a more simple skeletal structure (Hip, Knee, Ankle for the leg, and Neck, Shoulder, Elbow, Wrist for the arm); however, this system led to awkward bending and twisting at the hips and shoulders when doing more advanced animations (such as raising an arm above the head).

# Do I have to go through and merge every gender to every armor and to every head?  That seems like a lot of work…

I used a macro software (Auto Hotkey, I really like it) to do the hundreds of merges for each release.  It’s kind of difficult to explain, so if anyone is interested in doing this, I can do a tutorial on it, but you have to customize the macro for your own computer/screen resolution so it’s not just a download-and-go situation.