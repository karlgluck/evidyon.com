---
title:  A guide to Evidyon coding terminology
date:   2010-02-04
cover:  /media/header.png
---
I came up with terms to describe distinctions between various components in Evidyon (usually layers of content) so that they could be succinctly well-defined.  Below is a reference to these terms.  They're found throughout the code-base, and primarily in the "shared" folder.

**Image** - A raw data file that is a source of visual information.  Examples include .png, .bmp, .dds, and .jpg images, but this also referrs to auto-generated images such as those created by Perlin noise, a procedural algorithm or by mixing other images.

**Texture** - Defines a way of rendering an Image.  Multiple textures can use the same source image in different ways.  Types include static, sliding, circling and animated textures.  The water in Evidyon is a circling texture with alpha-blending attribute enabled.  The tree-leaves and grass have alpha-testing and alpha-blending enabled.  Particles render an Image using  a different blending mode so that they "blob" together into bright spots.

**Mesh** - A static collection of some number of groups of triangles for which each vertex is a GeometryVertex.  Evidyon uses .X files to represent Mesh objects.  Each group of triangles in a mesh is called a "subset".  Triangles can only belong to one subset.  A mesh can be re-scaled and modified when it is loaded.

**Scenery** - Similarly to how a Texture defines the rendering of an Image, Scenery defines the rendering of a Mesh.  Its main purpose is to link each mesh subset with a Texture that is used to render that subset.

**Animated Mesh** - An animated mesh is a collection of geometry in the Unseen Skinned Mesh format [[more on this format some other time]].  It is a very straightforward way of representing geometry that has vertices with influence weights for a skeletal hierarchy of animated bones.  Like a Mesh, it has no texture information but it does have texture groups.  It is interesting to point out that animated meshes also lack the animations themselves.   This is intentional because it is incredibly useful--and something that isn't available in any animated format I could easily use.  You'll only find one set of animations for all the avatars, for example, because they all share exactly the same animations since the skeletons are the same.

**Skeletal Animation** - Defines keyframe animations for one or more sets of AnimatedMesh objects.  Each bone's offset is in scale/rotate (quaternion)/translate form, and the full set of offsets on every bone is defined for every frame of the animation.

**Skinned Mesh** - Groups one or more Forms.  Each Form pairs an Animated Mesh with root scaling/transformation data and a set of skin Texture objects.  Also configures a set of Skeletal Animations that can be used for those forms.  Finally, sets the transform/source bone for pre-defined Attachment Points.

**Attachment Point** - Locations on a Skinned Mesh where objects with standard purposes (i.e. shield, helmet, boots, gloves, sword, off-hand weapon) can be attached.

**Actor Profile** - Brings a Skinned Mesh's Form to life by pairing its animations with specific meanings in the game (e.g. play anim3 on death, play anim1 to attack) and matching sound-queues (got hit, die, attack) to sounds.  This also stores the set of animations used in each Combat Profile.

**Combat Profile** - Based on an Actor's equipped items, a Combat Profile defining certain combat-specific animations is selected from the Actor Profile during game play.  For instance, an avatar wielding a 2H sword would use the "2H Weapon" Combat Profile.  Animation types defined in the profile include attack swings and combat stance.  This also defines attachment points for items when that profile is applied.  This is what puts the bow in the left hand for the bow animations, but the sword in the right-hand, and the pole-arm weapon in both.

**Lifeform AI** - Declares an implementation of an NPC.  A Lifeform AI references an Actor Profile to describe how it is to be displayed, but it also gives its visible name and game-mechanic attributes such as attack rates/damages, treasure, spawn effect, speed and visible equipment.

**VisualFX** - Definition of a simple particle effect, such as a fountain, explosion, or swirling ring.  Also generalizes to simple non-particle visual effects like dropping decals on the ground (e.g. footsteps when a character is walking) or rendering a Scenery instance.

**SpecialFX** - Combines one or more VisualFX with sound effects and positioning/animation data in a unique way to create the effect associated with some action.  This is used to create the look and sound for a spell.  SpecialFX can also have emitters that generate other special effects.  This type is also are used to represent the mouse-over-player effects and less obviously "special" effects like arrows and blood.

**Event** - An Event is an in-game instance of some SpecialFX description.  When the server does something, it generates some kind of  "create Event" notification, possibly with a unique ID, that is interpreted by each client.  Every Event has some lifetime, after which the client will automatically delete the event without notification from the server.  Some Event types, such as projectiles, can be explicitly addressed by their unique ID since their exact lifetime depends on whether or not they collide with something in the world.  Other events (most spell effects, for example) are never explicitly "terminated" by the server.

**Zone** - An area of the world characterized by a name and some attributes

**Map** - What contains all the data about the game world

**Map Mask** - Bitmap/PNG (lossless) image for which each color can be used to define something about the square of land at that map location.  Many masks are used to characterize a map.  For example, one mask can define where fluids (deep water, shallow water, acid pools, lava) are placed, another can define ground textures and yet another can define where to place scenery objects.

**Map Layer** - Used to construct the contents of a Map.  Usually, this is by associating a color in a Map Mask with some functionality, like placing a ground texture or wall, or changing the height of the land.  One frequently-used kind of Map Layer that doesn't do this is the terrain-blending layer, which replaces ground texture tiles along the edges between two fill areas with a nice border.  This causes grass to blend nicely into dirt, for example.

**Region** - A 16x16 section of the map.  Only regions with players in them or regions next to regions with players in them are active at any given time.

**Inhabitant** - A Lifeform AI that is always present in the world. If they die or are deactivated (because nobody is nearby) the inhabitant is recreated when a player approaches.  Examples include merchants and guards.

**Spawn** - Lifeform AI instances that are created randomly within active Regions.

**Navigability - Defines the movement attributes of a tile on the map.  Each type of navigability has its own characteristics.

**Trigger** - Something that causes an event.  Triggers are used to teleport players between maps when entering/exiting a dungeon; however, the framework exists for them to set off traps or trigger secrets.

**Item** - An object that can be owned by an avatar, traded, dropped on the ground (it has a visual representation) and used for some purpose.  Swords, shields, charms, potions and armor are all Items.

**Treasure** - Specification for how monsters drop randomly-generated items

**Magic** - Implementation of a kind of distinctive magical effect.  Direct-damage, area-of-effect (AOE), damage over time, portal, armor/speed enchantment, etc.  Also associates a Special FX with the casting of the Magic.

**Spell** - Wraps some number of Magics into the progression of a single Spell that can be used by the player.  Each stage, selected by the caster's avatar level, the Magic changes (but usually remains the same type) as does that Magic's associated Special FX.  Finally, this also gives an MP cost to the spell.  In this way, as a player levels up their spells start looking more and more powerful even though they don't change their names.