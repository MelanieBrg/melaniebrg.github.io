---
title: "Developing a Rollerball Game in Unity"
date: 2023-09-30
description: template
menu:
  #sidebar:
  #  name: Roller Ball Game
  #  identifier: unityUI
  #  parent: hci
  #  weight: 30
hero: rollerball.png
author:
  name: Mélanie Brégou 
  image: /images/author/me.png
math: true

---

### Introduction

In this article, I will walk you through the process of developing a rollerball game in Unity, where the player controls a ball on a plane, collecting stars while avoiding red enemies. My game includes both static and shooter enemies, a health system with three lives, and a Game Over screen that allows players to restart or exit the game. Let's dive into the development process step by step.

### Game development 

##### Create the Ground, Walls, and Ball

The initial step in crafting my rollerball game was setting up the game environment. I meticulously created a ground plane, enclosed it with walls to establish the play area, and strategically positioned the controllable ball at the center. 


##### Animate the Ball with a Script

Then I created a script to handle the ball's animation, allowing it to roll smoothly on the ground plane and respond to user input.


##### Collectibles Counter
The goal of the game is to collect as many stars as possible. To do so a counter is displayed in the user interface 


##### Health system

I implemented a three-lives health system, adding depth to the game's challenge. When a player lost all three lives, a "Game Over" screen would appear, offering the choice to either restart or exit the game. Unity's user-friendly UI system streamlined the process of creating this pivotal feature.


##### Shooting ennemy 
I designed two distinct types of enemies: static and shooter. The static enemy remained stationary, and contact with it led to a life loss. The shooter enemy, on the other hand, utilized Unity's AI Navigation system to pursue the player and shoot projectiles, adding an extra layer of challenge to the game.


##### Demonstration on Computer

Here is a little demo of the game :

{{< youtube ELBWRuksNbQ >}}


### Extension to mobile game

The game currently works on a computer, but the next step is to make it mobile-friendly. I tested it on an iPhone 14 Pro Max Emulator in Xcode. Here are the necessary steps:

1. Add the necessary modules: Unity Hub > Installs > Add Modules and add iOS build support.

2. Adjust the game for the emulator by changing the setting to Player Settings > Target SDK: Simulator SDK.

3. Open Xcode and launch the RollerBall app on the emulator.

{{< split 6 6>}}

<img src="/posts/hci/simple-unity-project/game_mobile.png" alt="face" height="500">


---

<img src="/posts/hci/simple-unity-project/game_mobile_game_over.png" >


{{< /split >}}

### Extension to VR game

I also built a version for a VR Hololens headset, following my professor's tutorial:

1. Install the OpenXR Plugin and XR Interaction Toolkit from the Package Manager (Unity Registry).

2. Go to Edit > Project Settings > XR Plug-in Management and enable OpenXR.

3. In the hierarchy, create an XR Origin by right-clicking: XR > XR Origin (VR).

4. Add Character Controller and Character Controller Driver to the XR Origin. Ensure that the Origin Base GO is set to XR Origin.

5. Delete the default main camera from the Hierarchy.

6. Right-click in the Hierarchy, go to XR > Locomotion System (Action based), and untick Teleportation and Snap Turn Provider. In the Add component, add Continuous Move and Continuous Turn Provider (action-based). Drag and drop the XR rig and Locomotion System. Make sure Input Action Manager is set in the XR Origin.

7. Set the hand XR controller parameters correctly.

8. Create an empty Prefab (HandController) in the Prefabs folder, creating a square and a cylinder to form a remote controller shape. Add it to the model prefab of the hand controller. Add a sphere collider to be able to grab objects. Add XR Direct Interactor and XR Grab Interactable to the PlayBoard.

9. Create an empty game object called AttachPoint and set it as the AttachTransform parameter.

Now you can immerse yourself in the game and use your hands as controllers.


<img src="/posts/hci/simple-unity-project/vr.png">

The next step, if time allows, is to create a room and make the playboard smaller to fit inside the room.







