---
layout: post
title: "CrabWorks"
image: /assets/img/Hero_low.png
---
CrabWorks is a swarm robotics project aimed at producing several robots that can communicate via light and perform complex
interactions. To reach our goal of complex motion, our team focused on the ability of our robots to play a game of tag: an interaction
that requires simple commands per bot but demonstrates the ability of our robots to create an advanced interaction.


## CrabBot
<img src="/assets/img/crabbot_low.png" style="width:400px;">
<!-- ![](/assets/img/crabbot_low.png) -->

Each robot has an array of photodiodes, a RGB led strip, and a 3-axis accelerometer to interact with environmental stimuli
and other robots. The photodiodes allow each robot to sense the relative location of other bots in its vicinity while the accelerometer
acts as a bump sensor to sense a tag.

## Mechanical Subsystem
![](/assets/img/exploded_view.png)

Since our goal was to create several of our little CrabBots, it was important that the mechanical design was able to be manufactured
 repeatedly and assembled quickly. Our final chassis was 3D printed to allow for rapid manufacturing and made liberal use of snap joints
 to make putting all the pieces together easy. There are also captive nuts in the chassis for a ‘screw together’ construction of the
 shell and battery housing.

## Electrical Subsystem
<img src="/assets/img/layout_rendered_low.png" style="width:400px;">
<!-- ![](/assets/img/layout_rendered_low.png) -->

To handle a large amount of sensors and outputs in a small package, we created a PCB to house all of the electrical components. The board contains:
*  An Atmega328PB
* Two Analog Multiplexers
* 3-Axis Accelerometer
* Linear Regulator
* Dual DC Motor Driver

A driving factor for the design of our PCB was the relatively short time scale of the project. To allow for simple programming, we decided to
use the same microcontroller that an Arduino uses: allowing us to compile code directly from the Arduino IDE Compiler.
