---
description: '[WORK IN PROGRESS]'
---

# Running NXP Gazebo

## Getting started

Once you've installed the NXP Gazebo stack, you can move on to running the example code provided in PX4 to self-drive the car around a simple track. At the end of the "Installation of NXP Gazebo" guide, we ran a command in our terminal that booted up the stack. As a reminder, here's the command:

```text
$ roslaunch nxp_gazebo nxp_cuprace.launch
```

When you run this command, you should see that the Gazebo simulation is booted up, and a PX4 shell is opened. Here's what it looks like:

![NXP Gazebo simulation booted up](../.gitbook/assets/image%20%2816%29.png)

The black terminal window is your PX4 shell, and the purple terminal window is the ROS console. The PX4 shell works just like a real PX4 shell - meaning that you can run your example programs and watch uORB topics just like you would on the real brushless NXP Cup car.

## Viewing the simulated Pixy camera

### Preface

In order to provide a true-to-life simulated environment for NXP Cup contestants, we have written a simulated Pixy camera module that detects lines and outputs vector data just like the real Pixy camera. The source code for the simulated Pixy camera uses OpenCV to fit vectors to detected lines in simulation.

### Guide

To view the output of the simulated Pixy camera, you can open a separate tab in your Ubuntu terminal window and run the following command:

```text
$ rqt_image_view
```

This will open a new window that shows the debug output of the simulated Pixy camera. Here's what it looks like:

![Simulated Pixy camera](../.gitbook/assets/image%20%2814%29.png)

{% hint style="info" %}
If you do not see the simulated Pixy camera output, use the drop down at the top left of the window and select /DebugDetectionImage.
{% endhint %}

The simulated Pixy camera detects the black lines in the environment and fits lines to to them. Then, it will use those lines to create a simulated Pixy camera vector output in the Pixy camera frame space as seen below:

![Pixy camera frame \(from https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:line\_api\)](../.gitbook/assets/image%20%2817%29.png)

As you can see in the simulated pixy camera output, the vector data returned is identical to the vector data that the real Pixy camera sends over I2C \(vector head and tail coordinates for each vector\). This allows contestants to use the same algorithms that are on their real NXP Cup cars.

The source code for this simulated Pixy camera is located at `~/git/nxp_ws/src/nxp_gazebo/scripts/track_vision.py`. You are free to edit this code if you see any potential areas of improvement!

## Running the example self-driving algorithm

To run the example self-driving algorithm, run the following command in the PX4 shell that is opened when you boot up the NXP Gazebo simulation:

```text
pxh> nxpcup start
```

When you run this command, a thread will be activated that should successfully drive the simulated NXP Cup car around the track.


