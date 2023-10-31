---
title: "3D platform game Unity"
date: 2020-06-08T08:06:25+06:00
description: Project
menu:
  sidebar:
    name: Unity 3D platform game
    identifier: platform-game
    parent: cg
    weight: 10
#tags: ["unity","game"]
hero: front.png
categories: ["unity"]
---
### Introduction


After a 12-hour class at the Institut Polytechnique de Paris, where we explored the fundamentals of Unity, Pauline Spinga and I embarked on a creative project to model and develop a **music-themed platform game named "Virtuoso"**. In this game, players step into the shoes of Vivaldi, a character who has lost his piano and guitar and must embark on a journey through the changing seasons to recover his instruments while collecting musical notes along the way.


{{< youtube 31kZ5MtXmck >}}

### 3D Modeling

Our journey began with 3D modeling using Blender. We crafted various elements such as the ground, bridges, trees, houses, mushrooms, and even a snowman. For the musical notes, we sourced a model from an external website. 
And we included our Blender modelisation projects : my guitar and Pauline's piano !


### Player Animation and Controls
To bring our character to life, we incorporated animations and controls. We obtained these assets from Mixamo, which provided both the character's appearance and animations.


### Health system

In "Virtuoso," players confront a formidable adversary – the snowman, who relentlessly hurls snow bullets at them. To intensify the gaming experience, we introduced a health system that equips the player with three lives. Each time a player is hit by a snow bullet, they lose one of their lives. Moreover, if the player inadvertently falls into the water, it results in an immediate game over.

### Music, Level Progression and User Interface

When you first launch the game, you will find yourself on the starting page, where you can choose to begin or quit the game. The game rules are clearly displayed for your reference.

Virtuoso is accompanied by Vivaldi's music, and the user interface provides essential information, displaying the player's remaining lives, the status of the piano and guitar (whether found or not), and the collected notes. Furthermore an exit button is available.

The game offers two distinct outcomes:

- When the player loses (due to falling into the water or running out of lives), a "Game Over" screen is displayed.
- On the other hand, when the player successfully recovers both instruments, they are greeted with a "Win" screen, and their level progresses, ranging from a novice musician to a virtuoso, based on the number of notes collected.


In either case, you have the option to return to the starting page or restart the game.

