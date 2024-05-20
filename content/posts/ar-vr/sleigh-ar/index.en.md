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

Introducing our AR game circuit developed using Unity3D and MRTK3 for HoloLens 2. This project was brought to life through a collaborative effort between myself and Pauline Spinga.

Here are the key steps of the project:

### Design

In designing the circuit within a ski station environment, we sourced various models from free3D, turbosquid, and sketchfab websites. Additionally, we crafted a custom panel featuring our school logo. All elements were assembled in Blender, with additional snow textures for ambiance.

<img src="/posts/ar-vr/sleigh-ar/front.png" height="200">

<img src="/posts/ar-vr/sleigh-ar/banc.png" height="200">

---

<img src="/posts/ar-vr/sleigh-ar/tsp.png" height="200">

<img src="/posts/ar-vr/sleigh-ar/trap.png" height="200">

However, during the application build for the HoloLens, we encountered performance issues due to the weight of the model. Consequently, we had to simplify the design elements.


### Game positionning 

To optimize user experience, we implemented a feature allowing players to adjust the position and scale of the circuit before gameplay. 
This adjustment can be made using hand gestures, facilitated by clicking on the "Game" button. Once satisfied with the positioning and scale, players can confirm their selection by pressing the "Done" button.

<img src="/posts/ar-vr/sleigh-ar/position.png" height="150">


### Game Control

Initially, we implemented a joystick Canva element for sleigh control. However, it was discovered that Canva elements are not compatible with the HoloLens headset. As a workaround, we replaced the joystick with four directional buttons (forward, backward, left, and right).

<img src="/posts/ar-vr/sleigh-ar/joystick.png" height="150">
<img src="/posts/ar-vr/sleigh-ar/controls.png" height="150">


### Levels and Gameplay

We created two levels, both measuring player performance by the circuit's chrono time and the collection of flakes along the track. At the end of each race, the score and time are displayed. Upon completing the first level, players have the option to replay it or progress to the second level. 

<img src="/posts/ar-vr/sleigh-ar/results.png" height="200">

In the second level, snow piles are introduced. Colliding with one of these snow piles results in the loss of one collected flake.

<img src="/posts/ar-vr/sleigh-ar/trap.png" height="200">

At each level, players can choose between two different sleigh designs.

<img src="/posts/ar-vr/sleigh-ar/sleighs.png" height="200">



### HoloLens Deployment

To deploy our application on the HoloLens headset we had the following build settings. In OpenXR Feature Groups we selected Microsoft HoloLens with Hand Tracking and Mixed Reality Features ticked.
There were the following interaction profiles:
- Microsoft Hand Interaction Profile
- Microsoft Motion Controller Profile
- Eye Gaze Interaction Profile

Once we built in Active(ARM64) platform with Active(Release) configuration, we connect the headset to the computer with a wire. We click on .snl file and open it in visual studio. Then in Project > properties > configuration properties > Debugging change the Machine Name. The machine name is in update and safety > developer mode > activate all togles to make ethernet work. Then enter the IP adress in machine name.


### HoloLens Deployment

To deploy our application on the HoloLens headset, we configured the following build settings. In the OpenXR Feature Groups, we selected Microsoft HoloLens with Hand Tracking and Mixed Reality Features enabled. The interaction profiles included:

- Microsoft Hand Interaction Profile
- Microsoft Motion Controller Profile
- Eye Gaze Interaction Profile

After building in the Active(ARM64) platform with the Active(Release) configuration, we connected the headset to the computer using a wire. Then, we opened the .snl file in Visual Studio. To ensure ethernet functionality, we activated all toggles in Update and Safety > Developer Mode (hololens). Next, we entered the IP address as the machine name in Project > Properties > Configuration Properties > Debugging.

### Conclusion and Further Improvements

Creating this game was not only enjoyable but also provided us with a great AR experience. However, there are several areas where we can further enhance the game:

- **Automatic Scene Positioning:** Implementing an automatic scene positioning feature would simplify the user experience, eliminating the need for manual adjustments.
  
- **Improved UI:** Enhancing the user interface with better button placement and overall design aesthetics would contribute to a more intuitive experience.
  
- **Enhanced Speed and Trajectory Control:** Improving speed control and trajectory adjustments would allow for smoother and more responsive gameplay, enhancing immersion and enjoyment for players.


Here is a short demo :

{{< youtube O9oJWZZlMic >}}