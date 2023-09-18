---
layout: post
title: "Automated Drone Charging"
image: /assets/drone_charging/4_pad.png
---

<img src="/assets/drone_charging/drone_on_pad.png" style="width:400px;">

One of the biggest challenges preventing drones from operating autonomously, 24/7 is the need to either swap or charge batteries. Either method can be a multi-step process requiring large amounts of mechanical precision: making the task of automating the process difficult. The following project centered around prototyping an automated charging pad that can operate without human intervention. To increase the ease of automation, this prototype aimed to alleviate the mechanical precision required to connect a charger to a drone battery. Instead of relying on a physical connector plugging into a battery, the following charging pad can route the battery terminals to a charger as along a drone can land in the arbitrarly large pad. 

An automated charging solution will be the most effective if the majority of the added components and complexity are on the charging side rather than the drone side. This keeps additional weight off of the drone and allows the charging concept to work with a potentially wide variety of drones. 

## Drone 

The main modification to the drone requires the terminals of the battery to be routed to the landing gear of the drone and exposed to the ground when charging. In the most simple configuration, there needs to be two contacts: one for the positive lead of the battery and the other for the negative lead. 

<img src="/assets/drone_charging/quad.png" style="width:400px;">

## Landing Pad

The landing pad is responsible for bridging the charging terminals of the drone to the controller board. The landing pad is also kept as simple as possible to allow the size of the pad to be easily scalable without additional cost. 

The landing pad is made out of copper tape cut into squares and attached to a cardboard sheet. The copper squares that are the same color in the following image are electrically connected. The size of the copper squares and the arrangement of the colors ensure that the positive and negative leads from the drone will come into contact with different colored squares: preventing the contacts from ever short circuiting. 

<img src="/assets/drone_charging/just_pad.png" style="width:400px;">

## Controller

The controller board is responsible for routing the copper squares in contact with the positive lead of the drone battery to the positive lead of the battery charger and likewise for the negative lead of the battery and charger. However, because the drone can land in any orientation on the charging pad, the controller has to sense what color copper square is connected to what lead of the drone's battery.

<img src="/assets/drone_charging/16_pad.png" style="width:400px;">

### Sensing Logic

The controller uses three bi-directional current sensors to determine the location of the battery terminals. On the controller, the four unique copper squares on the landing pad are connected as shown below with a resistor in series with a current sensor. As soon as the drone lands, a small current will flow from the positive side of the battery to the negative side through at least one current sensor. Depending on which current sensor is reading a positive, negative, or 0 current, the controller can determine which lead of the battery is connected to which color square on the landing pad. After the orientation is established, the controller, using an array of relays, can direct the positive and negative leads of the charger to the the positive and negative leads of the battery and initiate charging.

<img src="/assets/drone_charging/charging_logic.png" style="width:400px;">

### Circuit Design

I was able to build this prototype by designing a custom circuit board in KiCad that held all of the sensing logic and relays used to route the battery terminals to the charging terminals. Besides the sensing and switching logic, the circuit was controlled by an ESP32 breakout board. 

<img src="/assets/drone_charging/circuit_board.png" style="width:400px;">
