# Milestone 1 - Intro to NXP Gazebo and ROS

## Getting Started

Hello NXP Summer Camp participants! We are excited for you all to participate this summer and become familiar with the NXP Gazebo environment, ROS, and more. This page will explain the details of NXP Gazebo, how to install the software environment, and how to run the simulation for the first time. Let's get started!

## The NXP Gazebo environment

NXP Gazebo is built on top of the Robot Operating System, commonly referred to as ROS. ROS allows us to create a true-to-life model of the entire NXP Cup environemnt - including the car, tracks, and obstacles. 

![Image of the simulated NXP Cup Car](<../../.gitbook/assets/image (43).png>)

We also have been able to create a simulated Pixy Camera for use in simulation so your existing algorithms will work similarly to how they work on your real NXP Cup Car. 

![Simulated Pixy Camera](<../../.gitbook/assets/image (44).png>)

The underlying platform for self-driving code is a ROS node. This node can be programmed in either C++ or Python. C++ will be more familiar to NXP Cup participants, but Python can be faster to prototype and test with due to the vast number of libraries available. Two ROS packages will be provided - one in Python and one in C++.

## Installing the NXP Gazebo environment

The NXP Gazebo environment is simple to install - you just need to run a script and a few commands. We have prepared a full guide for doing so on your machine. You can follow the link below to go to the guide and get started!

{% hint style="warning" %}
NOTE: You MUST be running Ubuntu 20.04 in either a Virtual Machine or in a native install. This simulation is not supported on any other operating system.
{% endhint %}

{% content-ref url="installation-of-nxp-gazebo-1.md" %}
[installation-of-nxp-gazebo-1.md](installation-of-nxp-gazebo-1.md)
{% endcontent-ref %}

## Running the NXP Gazebo environment

Once you have installed NXP Gazebo, you can now run it on your machine! Please go to the link below to get started.

{% content-ref url="running-nxp-gazebo.md" %}
[running-nxp-gazebo.md](running-nxp-gazebo.md)
{% endcontent-ref %}

## Deliverables

For the 2nd Milestone call, participants will create a 5-10 minute video of their progress. We would like to see the following checklist items in your video:

* [ ] Documentation of participants installing NXP Gazebo with feedback - was it easy to install? Hard? Let us know!
* [ ] Running the NXP Gazebo environment - How does it run on your machine? Is your real-time factor 1.0? What's your fps? Did the vehicle spawn correctly and begin driving using the example line follower node?
