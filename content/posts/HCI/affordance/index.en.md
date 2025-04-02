---
title: "Affordance in daily life"
date: 2023-09-30
description: template
menu:
  #sidebar:
  #  name: Affordance in daily life
  #  identifier: affordance
  #  parent: hci
  #  weight: 30
hero: vox_front.jpg
author:
  name: Mélanie Brégou 
  image: /images/author/me.png
math: true
draft: true
show: false 
hide: true
---


After a 6-hour lecture introducing Human-Computer Interaction (HCI), our first homework was to find real-life objects that exemplify the concepts in HCI.

### Affordances

##### Definition

Before we delve into real-life examples, let's define what an affordance in HCI. Affordance refers to the inherent **usability or functionality of an object, interface, or system**. It's a concept that suggests what actions can be performed with an object and how those actions can be intuitively understood by users. 

##### Good Affordance Example: The Guitar Stand

<img src="/posts/hci/affordance/stand_guitar.jpg" alt="front" height="250" style="float: left; margin-right: 10px;" >

One excellent example of a good affordance is a simple guitar stand. Indeed, the guitar stand provides a clear and intuitive affordance for users to place their guitars securely. 
- The mapping of where to place the guitar on the stand is straightforward. The shape of the stand corresponds to the shape of the guitar, making it easy to understand how to position the instrument.
- When you place a guitar on the stand, you feel a sense of stability and support. This feedback reinforces the understanding that the stand is designed for this purpose.



##### Bad Affordance Example: The Complex Guitar Amplifier



On the other hand, let's consider a guitar amplifier with an abundance of buttons and controls as an example of a bad affordance. 

- While the amplifier's purpose is clear—to amplify the guitar's sound—the multitude of buttons, knobs, and switches can overwhelm users, making it challenging to determine their functions at a glance.

- The mapping between the controls and their effects on the sound may not be immediately evident. Users may need to consult a manual or experiment extensively to understand how to achieve their desired sound.


{{< split 6 6>}}

<img src="/posts/hci/affordance/vox_front.jpg" alt="front" >


---


<img src="/posts/hci/affordance/vox_buttons.jpg" alt="front" style="margin-top: 90px" >

{{< /split >}}


######  How to Improve the Guitar Amplifier's Affordance
To enhance the affordance of the guitar amplifier, several improvements can be made:
- Simplify Controls: Reduce the number of controls and group related functions together. Use labels and icons to make the purpose of each control more apparent.
- Visual Feedback: Incorporate more LED indicators or display screens to provide real-time visual feedback on the settings' impact on sound.



### Gestalt Laws

#### Definition
The Gestalt principles, developed by German psychologists, explain how humans interpret their complex surroundings. These principles help us understand why we perceive certain visual and auditory phenomena and make sense of seemingly chaotic information. There are six fundamental Gestalt principles:

- **Similarity**: Similar things tend to appear grouped together, both visually and auditorily. We naturally group objects based on their similarity, such as color or sound.
- **Prägnanz**: This principle, also called the law of simplicity, suggests that our brains simplify complex objects into recognizable forms. For example, we see the Olympic logo as overlapping circles, not complex lines.
- **Proximity**: Objects physically close to each other are seen as more related. This leads to the grouping of nearby elements.
- **Continuity**: Points connected by smooth lines are perceived as related. Elements along a line or curve are seen as more connected.
- **Closure**: We perceive elements as belonging together if they complete some entity, even with missing information. Our brains fill in gaps to create meaningful patterns.
- **Common Region**: Elements within the same closed region are seen as related. This principle explains why elements within a defined boundary appear connected.


#### Examples

Here are examples of website which do not respect these laws.

##### Userinyerface
The game [Userinyerface](https://userinyerface.com/game.html) is a prime example of a digital interface that intentionally disregards several Gestalt Laws, creating a frustrating and confusing user experience.
If you try the game you will observe that it introduces complexity and confusion in its design, challenging the notion of simplicity (Prägnanz), visual elements do not follow smooth paths or logical sequences, further adding to the disorienting experience (Continuity), consistency in color, shape, and styling is intentionally disrupted to defy user expectations (Similarity).

The game therefore highlights the importance of following Gestalt principles in real-world design to create user-friendly and intuitive interfaces.

##### Moodle website

Another example, though less critical than the game, is the login experience on the Moodle website where courses are accessed. The website design disregards Gestalt principles, leading to a potentially frustrating user experience.

Problem: The "Connexion" (Login) button is tiny and has light text and color, making it less prominent (Prägnanz). After clicking it, users are directed to a page where they need to choose their school, introducing an unexpected step that disrupts the Law of Closure.

{{< split 6 6>}}

<img src="/posts/hci/affordance/moodle_conn1.png" alt="conn1" >


---


<img src="/posts/hci/affordance/moodle_conn2.png" alt="conn2" >

{{< /split >}}



Correction: To enhance the user experience and align the design with Gestalt principles, consider implementing the following changes:

- Button Visibility: Increase the visibility of the "Connexion" button by using a contrasting color, a larger font size, or bold text to make it more prominent. This makes it easier for users to identify and initiate the login process.
- Streamline Login: Aim to simplify the login process. Direct users to the login form immediately after clicking the "Connexion" button. If school selection is necessary, integrate it into the login form as a dropdown menu or a clear, concise choice, rather than leading users to a separate page.




### Dark designs

***"A dark pattern is a type of user interface that appears to have been carefully crafted to trick users into doing things that are not in their interest and is usually at their expense."*** Harry Brignull, a London based UX designer.

##### Forced Continuity

When you have to start your free trial by adding your card details, or you need to enter your email to continue using a website or an app. Choosing to skip these self-interest gimmicks is not an option in forced continuity.

To improve the design :
- Transparent Cart
- Explicit consent
- Confirmation

##### Roach Motel

The Roach Motel design pattern makes it easy for users to sign up for a service or subscription but incredibly difficult for them to cancel or unsubscribe. 


To redesign for an ethical use : 
- Clear Cancelation Process
- Confirmation and Feedback
- Transparent Pricing






