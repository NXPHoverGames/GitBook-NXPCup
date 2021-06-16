# Running NXP Gazebo

## Booting up Gazebo

Once you've installed NXP Gazebo, you can move on to running the example code provided to self-drive the car around a simple track. At the end of the "Installation of NXP Gazebo" guide, we ran a command in our terminal that booted up the stack. As a reminder, here's the command:

```text
$ ros2 launch sim_gazebo_bringup sim_gazebo.launch.py
```

When you run this command, you should see that the Gazebo simulation is booted up, and the example self-driving node starts automatically. 

![](../.gitbook/assets/image%20%2841%29.png)

The simulation will start a program that allows you to view the simulated Pixy camera output. This is for debug use to make sure the vision node is working correctly. This is explained in the next section.

## Viewing the simulated Pixy camera

### Preface

In order to provide a true-to-life simulated environment for NXP Cup contestants, we have written a simulated Pixy camera module that detects lines and outputs vector data just like the real Pixy camera. The source code for the simulated Pixy camera uses OpenCV to fit vectors to detected lines in simulation.

### Guide

The simulation stack will open a new window that shows the debug output of the simulated Pixy camera. Here's what it looks like:

![Simulated Pixy camera](../.gitbook/assets/image%20%2814%29.png)

{% hint style="info" %}
If you do not see the simulated Pixy camera output, use the drop down at the top left of the window and select /debugImage0.
{% endhint %}

The simulated Pixy camera detects the red lines in the environment and fits lines to to them. Then, it will use those lines to create a simulated Pixy camera vector output in the Pixy camera frame space as seen below:

![Pixy camera frame \(from https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:line\_api\)](../.gitbook/assets/image%20%2817%29.png)

As you can see in the simulated pixy camera output, the vector data returned is identical to the vector data that the real Pixy camera sends over I2C \(vector head and tail coordinates for each vector\). This allows contestants to use the same algorithms that are on their real NXP Cup cars.

The source code for this simulated Pixy camera is located at `~/ros2ws/src/nxp_cup_vision/nxp_cup_vision/nxp_track_vision.py` ​. You are free to edit this code if you see any potential areas of improvement!







