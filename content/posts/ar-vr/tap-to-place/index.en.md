---
title: "Tap to Place App"
date: 2023-11-10
description: Project
menu:
  sidebar:
    name: Tap to Place App
    identifier: tap-to-place
    parent: ar-vr
    weight: 40
#tags: ["unity","game"]
hero: front.png
categories: ["ar","mobile", "game", "unity", "ARFoundation"]
---

In the context of our AR course at Institut Polytechnique de Paris, we were asked to develop a mobile application with AR Foundation in Unity to place object on the ground by taping its desired place on the screen.

<video width="640" height="360" controls>
  <source src="tap-to-place.mov" type="video/quicktime">
  Your browser does not support the video tag.
</video>



Here are the different steps of the project :

#### Unity settings 

In order to make the application work on my Iphone I tried several Unity versions but the one which worked was the 2022.3.10f1.
Then create a new project with AR Mobile Core template 

<img src="/posts/ar-vr/tap-to-place/setup.png" height="300">

#### Place Item script 

Write and put the following script with a prefab in the XR origin.

```c#
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.XR.ARFoundation;
using UnityEngine.XR.ARSubsystems;
using EnhancedTouch = UnityEngine.InputSystem.EnhancedTouch;

[RequireComponent(typeof(ARRaycastManager), typeof(ARPlaneManager))]
public class PlaceItem : MonoBehaviour
{
    [SerializeField]
    private GameObject prefab;

    private ARRaycastManager arRaycastManager;
    private ARPlaneManager arPlaneManager;
    private List<ARRaycastHit> hits = new List<ARRaycastHit>();

    private void Awake()
    {
        arRaycastManager = GetComponent<ARRaycastManager>();
        arPlaneManager = GetComponent<ARPlaneManager>();
    }

    private void OnEnable()
    {
        EnhancedTouch.TouchSimulation.Enable();
        EnhancedTouch.EnhancedTouchSupport.Enable();
        EnhancedTouch.Touch.onFingerDown += FingerDown;
    }

    private void OnDisable()
    {
        EnhancedTouch.TouchSimulation.Disable();
        EnhancedTouch.EnhancedTouchSupport.Disable();
        EnhancedTouch.Touch.onFingerDown -= FingerDown;
    }

    private void FingerDown(EnhancedTouch.Finger finger)
    {
        if (finger.index != 0) return; // Pas de multi-touch

        if (arRaycastManager.Raycast(finger.currentTouch.screenPosition, hits, TrackableType.PlaneWithinPolygon))
        {
            foreach (ARRaycastHit hit in hits)
            {
                Pose pose = hit.pose;
                Instantiate(prefab, pose.position, pose.rotation);
            }
        }
    }
}
```

