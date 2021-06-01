---
description: '[WORK IN PROGRESS]'
---

# Introduction to NXP Gazebo Summer Camp

## Summer Camp

Hello and welcome to the NXP Gazebo Summer Camp! This event is designed to familiarize NXP Cup participants with the NXP Gazebo simulation environment for NXP Cup. The simulation environment will allow NXP Cup contestants to design, prototype, and test their NXP Cup software in a rapid fashion without the risk of damaging their NXP Cup cars. 

This Gitbook contains all of the necessary documentation for installing, running, and building your NXP Cup car in NXP Gazebo. Use the context menus on the left to go through each section of the guide.

For information on System Requirements, Milestones, and more, read below!

## What's Gazebo?

![](../.gitbook/assets/image%20%2810%29.png)

Gazebo is a full-fledged simulation environment that is compatible with PX4. In 2021, NXP Cup contestants may use the Gazebo simulation for an extra challenge at home. The benefit to using the Gazebo simulation environment is that you can test your code without crashing or damaging your actual NXP Cup car. The code modules that you run on your actual NXP Cup car can be ported to the Gazebo simulation environment \(and vice versa\) with ease - and if you're using a brushless Cup car, you'll essentially be running the same exact code.

## Can I run NXP Gazebo?

See the minimum and recommended system requirements below to see if you can run NXP Gazebo.

{% hint style="warning" %}
It is HIGHLY RECOMMENDED that you run NXP Gazebo in a native Ubuntu installation! Virtual Machine performance can vary greatly from machine to machine and can produce inconsistent simulation results!
{% endhint %}

Minimum Requirements:

* **CPU**: Quad-core Intel or AMD mobile processor or better \(i.e. Intel i5-8550U or AMD Ryzen 5 3500U\)
* **GPU**: Intel UHD Graphics or better
* **RAM**: 8GB \(Native Ubuntu\) / 16GB \(Virtual Machine\)
* **Storage**: 50GB \(SSD highly recommended\)

Recommended Requirements:

* **CPU**: Quad-core Intel or AMD desktop processor or better \(i.e. Intel i5-9400F or AMD Ryzen 5 2600\)
* **GPU**: Dedicated Nvidia or AMD GPU \(i.e. Nvidia GTX 1060 or AMD RX 480\)
* **RAM**: 16GB \(Native Ubuntu\)
* **Storage**: 50GB \(SSD highly recommended\)

## Milestones

Throughout the NXP Gazebo Summer Camp, contestants will be required to meet four milestones within simulation. The milestones are as follows:

### Milestone 1

1. Kick-off
   1. Obtain learning materials, documentation, videos, and more!

### Milestone 2

1. Learn about Gazebo, ROS, PX4, and the NXP Gazebo environment

### Milestone 3

1. Drive around the octagon track autonomously
2. Stop for a stop sign for 3 seconds and then continue

### Milestone 4

1. Avoid a stationary object obstructing the track
2. Recognize a 4-way intersection and turn right
3. Recognize a moving object crossing the track and wait for it to cross

## How do I start?

Continue to the next section to start installing the required software for the Gazebo simulation environment. Soon you will be running the environment shown below!

![NXP Cup Car in Gazebo Simulation](../.gitbook/assets/image%20%2811%29.png)

{% page-ref page="../archive/installation-of-nxp-gazebo.md" %}

