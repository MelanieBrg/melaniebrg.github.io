---
title: "Snow sleigh game on Hololens2"
date: 2024-01-30
description: Project
menu:
  sidebar:
    name: Snow sleigh Hololens
    identifier: sleigh-ar
    parent: ar-vr
    weight: 30
#tags: ["unity","game"]
hero: front.png
categories: ["ar","hololens", "game", "unity", "MRTK"]
---

Check out this short demo of an AR game circuit, utilizing Unity3D and MRTK3 for Hololens2. The project was conceived and executed by Pauline Spinga and myself:

{{< youtube O9oJWZZlMic >}}



Here are the major steps of the project :

### Design

In designing the circuit within a ski station environment, we sourced various models from free3D, turbosquid, and sketchfab websites. Additionally, we crafted a custom panel featuring our school logo. All elements were assembled in Blender, with additional snow textures for ambiance.

<img src="/posts/ar-vr/sleigh-ar/front.png" height="200">

<img src="/posts/ar-vr/sleigh-ar/banc.png" height="200">

---

<img src="/posts/ar-vr/sleigh-ar/tsp.png" height="200">

<img src="/posts/ar-vr/sleigh-ar/trap.png" height="200">

However, during the application build for the Hololens, we encountered performance issues due to the weight of the model. Consequently, we had to simplify the design elements.


### Game positionning 

To optimize user experience, we implemented a feature allowing players to adjust the position and scale of the circuit before gameplay. 
This adjustment can be made using hand gestures, facilitated by clicking on the "Game" button. Once satisfied with the positioning and scale, players can confirm their selection by pressing the "Done" button.

<img src="/posts/ar-vr/sleigh-ar/position.png" height="150">


### Game Control

Initially, we implemented a joystick Canva element for sleigh control. However, it was discovered that Canva elements are not compatible with the Hololens headset. As a workaround, we replaced the joystick with four directional buttons (forward, backward, left, and right).

<img src="/posts/ar-vr/sleigh-ar/joystick.png" height="150">
<img src="/posts/ar-vr/sleigh-ar/controls.png" height="150">


### Levels and Gameplay

We created two levels, both measuring player performance by the circuit's chrono time and the collection of flakes along the track. At the end of each race, the score and time are displayed. Upon completing the first level, players have the option to replay it or progress to the second level. 

<img src="/posts/ar-vr/sleigh-ar/results.png" height="200">

In the second level, snow piles are introduced. Colliding with one of these snow piles results in the loss of one collected flake.

<img src="/posts/ar-vr/sleigh-ar/trap.png" height="200">

At each level, players can choose between two different sleigh designs.

<img src="/posts/ar-vr/sleigh-ar/sleighs.png" height="200">


### Conclusion and Further Improvements

Creating this game was not only enjoyable but also provided us with a great AR experience. However, there are several areas where we can further enhance the game:

- **Automatic Scene Positioning:** Implementing an automatic scene positioning feature would simplify the user experience, eliminating the need for manual adjustments.
  
- **Improved UI:** Enhancing the user interface with better button placement and overall design aesthetics would contribute to a more intuitive experience.
  
- **Enhanced Speed and Trajectory Control:** Improving speed control and trajectory adjustments would allow for smoother and more responsive gameplay, enhancing immersion and enjoyment for players.
