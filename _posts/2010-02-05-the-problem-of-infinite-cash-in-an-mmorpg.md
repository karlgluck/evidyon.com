---
title:  The Problem of Infinite Cash in an MMORPG
date:   2010-02-05
cover:  /media/header.png
excerpt: This is the problem of inflation in an MMORPG and our solution!
---
The process:

1. Kill monsters for loot
2. Liquidate loot for money
3. Repeat

This is the problem of inflation in an MMORPG.

Currency is inflated, giving those with a lot of time to put into the game (or write bots) a huge advantage
1. It's hard to set a fixed price for merchants of items, since the currency's value is constantly changing
2. To counteract an item being overpowered because more money keeps piling into the system to purchase the item, a dev has to limit its availability (driving up the p2p price), nerf the item's attributes or increase the purchase price to keep up with inflation.  These solutions result in items that are either so hard to obtain that they might as well not exist for the average player, or they're mostly useless.
3. It's hard to set up a trading system where currency is more than just filler
4. The result of killing a monster is some form of material reward.  If it is easy to liquidate this reward and stockpile it, the above scenario is unavoidable.  It can be controlled somewhat with non-drop/non-trade items or having monsters only drop a limited amount of loot, but neither is a stable solution.  Furthermore, it was our opinion that having ND/NT items would break the fun of a game somewhat.  What sense does it make that you can't put down your sword?  Is it glued to your hand or something?

Besides, as long as there is demand for money (which is the whole point of its existence) there is always some finite fraction of players who are willing to commit huge amounts of time to gaming the system by which it is acquired.  If you make loot low, they'll just kill a massive number of monsters.  If you make items NDNT, they'll trade in the non-NDNT ones.  If you don't have any non-NDNT items, players can never trade with each other--which is a big part of an MMORPG.  If you tax the money they stockpile, they'll spread it over as many accounts as necessary so as not to be penalized.  If you make durability a big enough factor to matter, they'll be often annoyed when they get penalized; if it's not that significant, it isn't strong enough to soak up extra cash.  All of these extra rules make the game more confusing and, in my opinion, seem restrictive and less fun to play.

Wouldn't it be nice if there were a way to solve this problem in an elegant, simple way?

Our solution is the Geonite/Bazaar system.  The key to solving the problem of infinite money was not to create artificial limitations, but instead to remove artificial extensions to the in-game economy--namely, the ease of liquidating items.

First, the main issue with having monsters drop lots of items was that these items all have to go somewhere.  Players generally horde the good stuff, but what constitutes "good stuff" depends on the player's level.  Given that high level and low level characters coexist--and what is junk to one is a prized possession to the other--simply not offering money for goods of a certain type (or reducing the amount of money based on the seller's avatar level) is not a solution.

For the sale of items, I implemented the Bazaar.  By this mechanism, players can trade items for gold with other players via listings, somewhat like the Amazon Marketplace.  This way, the currency-value is relatively stable (and accurate) since the price is based on the real supply and demand for the item.  The Bazaar skims some money off the top via a listing fee, so the system does actually "leak" money.  This process is also much slower than selling a bunch of junk to a NPC merchant, so players are implicitly encouraged only to list stuff that someone might actually want.

So what about the junk items that need to be eliminated?  There is something for this as well.  The main problem with easily liquidating items is not that the items are being converted into a uniform measurement of value, but that the value can be transferred.  When a player "sacrifices" items for Geonite, that player is the only one that is able to use the Geonite to perform actions.  In an early version of Evidyon, Geonite was a player attribute that allowed them to use special abilities or trigger world events.  In the current version, Geonite is used to trigger the special abilities of Geosids (the big crystals in the game).  This allows non-consumable items to be "consumed" by the system without resulting in inflation.

Money becomes overabundant and worthless