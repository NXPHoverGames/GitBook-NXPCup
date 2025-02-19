---
description: '[WORK IN PROGRESS]'
---

# Overview of the NXP Gazebo stack \[OLD]

## Summary

This page is designed to help contestants understand the inner-workings of the NXP Gazebo simulation stack. As a contestant, you will only need to focus on a small set of files within this massive workspace. In order to reduce confusion, we have created a detailed outline of all of the files and folders in the stack, and have documented the specific files and folders that contestants will be working with in order to write self-driving algorithms for their simulated NXP Cup car.

## Outline of the stack

The NXP Gazebo simulation stack uses a diverse set of software to enable the simulation of the Cup car. Thankfully, as NXP Cup contestants, you will only need to use specific portions of the stack to develop your self-driving software. The stack is located in the `~/git/` folder and is set up as follows:

![](<../.gitbook/assets/image (38) (1).png>)

| Folder               | Purpose                                                             |
| -------------------- | ------------------------------------------------------------------- |
| build                | ROS2 specific build folder.                                         |
| install              | ROS2 specific install folder.                                       |
| log                  | ROS2 specific log folder.                                           |
| NXP-Autopilot        | Full source code of PX4. This is where self-driving code will live. |
| nxp\_gazebo          | Scripts and model files for simulation.                             |
| nxp\_gazebo\_plugins | Necessary plugins for Gazebo                                        |
| osrf                 | OSRF 3D model library for creating custom worlds                    |
| src                  | See the next section for an overview                                |

### src folder contents

The src folder within the ROS2 workspace contains some PX4 specific ROS packages as well as the `sim_gazebo_bringup` package.

![](<../.gitbook/assets/image (39) (1).png>)

| Folder                           | Purpose                                                                                           |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| nxp\_cu&#x70;_\__&#x76;ision     | Contains the OpenCV vision code for simulating Pixy camera to detect lines                        |
| px4\_msgs                        | Contains PX4 uORB message definitions for RTPS                                                    |
| px4\_ro&#x73;_\__&#x63;om        | Contains the code necessary for transporting PX4 messages over RTPS                               |
| sim\_gazeb&#x6F;_\__&#x62;ringup | Contains scripts for booting up the Gazebo simulation as well as setting up the simulation stack. |

### Writing self-driving code

To write self-driving code for the simulated NXP Cup car, you must be familiar with how PX4 runs modules. A brief overview will be be outlined in this section.&#x20;

To develop your self-driving code, you'll want to navigate to the NXP-Autopilot directory. This directory contains the PX4 firmware. A look inside the NXP-Autopilot directory is below:

![\~/git/PX4-Autopilot](<../.gitbook/assets/image (13) (1) (1).png>)

While there is a large amount of files and folders inside the PX4-Autopilot directory, there is only a single location that you need to use. The location is in the `~/ros2ws/NXP-Autopilot/src/examples` directory. This directory contains user-written and example modules for PX4. By placing your self-driving source code in this directory, you can easily add it to the PX4 SITL (Software In The Loop) build target. Thankfully, we have already included a simple example module that drives the simulated cup car around an oval track. The module is located at `~/ros2ws/NXP-Autopilot/src/examples/nxpcup/`. An overview of the directory is located below:

![\~/git/nxp\_ws/src/Firmware/src/examples/nxpcup/](<../.gitbook/assets/image (34) (1) (1).png>)

Inside of the `nxpcup` directory, you will see a few files that may look familiar if you have previously used a brushless NXP Cup car kit. The files here are provided for contestants to get a quick start with simulation. A description of each file is in the table below:

| File name        | Description                                                                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| CMakeLists.txt   | Tells cmake what files to compile for this module. This does not need to be changed unless you add extra source files.                                                   |
| nxpcup\_work.cpp | This file starts a thread that runs the simulated NXP Cup car. Code here does not need to be changed.                                                                    |
| nxpcup\_work.h   | Header file for the nxpcup\_start.cpp file. Does not need to be changed.                                                                                                 |
| nxpcup\_race.cpp | This file contains the self-driving source code. This is the file that you will use to develop your self-driving algorithms.                                             |
| nxpcup\_race.h   | Header file for the nxpcup\_race.cpp file. If you add functions, structures, or other code that needs to be contained in a CPP header file, you will put that code here. |

### Overview of the example code

Inside of `nxpcup_race.cpp`, there is a function that receives vector information from the a simulated Pixy camera and returns speed and steer values. The vector information is received through a uORB topic and is nearly identical to the vector information sent by the Pixy over I2C.&#x20;

{% hint style="warning" %}
At the moment, only up to two vectors are published to the uORB topic the example code subscribes to. In the future, we plan to support more than two vectors as well as intersection data so that the simulated Pixy cam is a 1-to-1 replacement in the code.
{% endhint %}

The source code uses a simple algorithm to extract speed and steer values from the supplied vector data to drive the car. We expect contestants to improve upon this algorithm and show us how fast their simulated NXP Cup car can go!&#x20;

## Feedback

If you run into any discrepancies with this page, please contact us using the Contact page. A link to it is below.

{% content-ref url="../welcome-to-nxp-cup.md" %}
[welcome-to-nxp-cup.md](../welcome-to-nxp-cup.md)
{% endcontent-ref %}

## Next steps

In the next section, we will outline the steps to running this example code. Please follow the navigation at the bottom of the page or use the menu to the left.
