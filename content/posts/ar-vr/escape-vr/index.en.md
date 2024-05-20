---
title: "Escape Game in VR"
date: 2024-01-30
description: Project
menu:
  sidebar:
    name: Escape Game VR
    identifier: escape-vr
    parent: ar-vr
    weight: 35
#tags: ["unity","game"]
hero: front.png
categories: ["vr","metaquest", "game", "unity", "escape"]
---

Discover our virtual reality (VR) escape game, crafted by Mélanie Brégou and Pauline Spinga. 
Inspired by fantastic universes and Unity Store's Escape Room assets, we have developed original enigmas: from recreating melodies to assembling puzzles, all to unravel clues for escaping our magical-themed house.

{{< youtube Up3RjfBAd6I >}}

## Set Up

To begin our VR game development journey, we meticulously set up our project environment in Unity. Here's a step-by-step guide on how we initiated the project:

1. **Creating the Project**: We started by creating a new 3D project in Unity using the following specifications:
   - Unity version: 2022.3.2f1
   - Template: 3D

2. **Configuring XR Plugin Management**:
   - Navigate to `Edit > Project Settings > XR Plugin Management`.
   - Install XR Plugin Management if not already installed.
   - Open XR Plugin Management and confirm to restart Unity.
   - Upon restart, address any issues by:
     - Editing the `Interaction Profiles` for the Oculus Touch Controller Profile.
     - Clicking on "Fix" to resolve any Input System issues.

3. **Installing XR Interaction Toolkit**:
   - Open the `Window` menu and select `Package Manager`.
   - Choose the `Unity Registry` and locate `XR Interaction Toolkit`.
   - Install XR Interaction Toolkit.
   - Import the "Starter Assets" from the samples provided.

4. **Setting Up XR Origin**:
   - Add the XR Origin asset to the project's assets.

5. **Removing Default Camera**:
   - Delete the default Main Camera as it will be replaced with VR camera setups.

6. **Integrating Escape Room Assets**:
   - We incorporated the "Escape Room" free asset from the Unity Asset Store.
   - Customized the environment by removing unnecessary elements and puzzles to craft our unique gaming experience.



## Enigmas

### Piano

Players start in a room with a wall. They must reproduce a specific melody of the radio on the piano to make the wall disappear. 
{{< split 3 3 >}}


<img src="/posts/ar-vr/escape-vr/wall.png" >

---

<img src="/posts/ar-vr/escape-vr/radio.png" >

---

<img src="/posts/ar-vr/escape-vr/piano.png" >



{{< /split >}}



### Puzzle

Upon solving the piano enigma, players gain access to another room where puzzle pieces are hidden. These pieces, designed using Blender, provide a hint for the next action. Assembling the puzzle also reveals a key. 

<img src="/posts/ar-vr/escape-vr/puzzle.png" height="250">


### Incendio

The obtained key opens a drawer containing a wand. Utilizing a script from the escape room asset, players can interact with the drawer. With the wand and an image of the puzzle, players can deduce its fire-making ability. By approaching the fireplace with the wand, players trigger an animation of a parchment with the "Alohomora" inscription.


<img src="/posts/ar-vr/escape-vr/fire.png" height="250">

### Alohomora

Referencing the Harry Potter universe, "Alohomora" is a spell that opens doors. Similar to "Incendio" players must approach the door with the wand to unlock it.

<img src="/posts/ar-vr/escape-vr/alohomora.png" height="250">


## Start and End Menu

We implemented a simple menu to launch the game and included an end/restart button upon completing the game.

{{< split 6 6>}}

<img src="/posts/ar-vr/escape-vr/start.png" height="250">

---
<img src="/posts/ar-vr/escape-vr/end.png" height="250">


{{< /split >}}


## Player Movements

In our VR game developed in Unity, player movements are facilitated through a combination of continuous locomotion and teleportation mechanics.

### Continuous Movements

Continuous movements allow players to navigate the virtual environment seamlessly. To implement this, we utilized the XR Interaction Toolkit along with the Starter Assets. Here's a guide:

1. **XR Interaction Toolkit Setup**: Navigate to `Samples > XR Interaction Toolkit > 2.3.2 > Starter Assets`. Add the `XRI Default Left Controller` component to the `ActionBasedController` object. Repeat the same process for the right hand controller. In our game we chose to have 'snap turns' on the left joystick and continuous movement on the right joystick.  

2. **XR Origin Configuration**: In the `Project Settings`, access the `Preset Manager`. In the `Find` section, input "Right" and "Left", then remove and re-add the `XR Origin`. Ensure all fields are properly filled.

3. **Animated Hands**: We enhanced the immersive experience by integrating animated hands. We dowloaded them via our Unity teacher.

### Teleportation Mechanism

In addition to continuous movements, our game features teleportation for quick navigation and strategic positioning. 

- **Teleportation Areas**: We designated specific areas within the virtual environment where players can teleport. 

![Teleportation Area](/posts/ar-vr/escape-vr/tp.png)



## Optimization

Our primary goal was to maintain a performance of above 70FPS to provide a smooth experience and mitigate motion sickness. We achieved this by removing unnecessary decoration assets, baking lighting, and implementing occlusion culling.


## Conclusion and Further Improvements

We conducted several iterations to refine our VR escape game on MetaQuest, ensuring an immersive and enjoyable experience for players. Moving forward, we plan to continue improving the game by refining existing enigmas and adding speech recognition for spells.
