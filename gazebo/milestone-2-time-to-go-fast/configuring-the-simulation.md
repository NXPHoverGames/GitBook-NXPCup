# Configuring the simulation

NXP Gazebo is highly configurable. The main repository, `sim_gazebo_bringup`, uses a ROS2 launch file to boot the simulation. This launch file can be configured with a JSON file contained within the package. This page will give an overview of the "gen\_params.json" file and how to make changes to the simulation using it.

## General Parameters File Overview

The general parameters file can be found at "~/ros2ws/src/sim\_gazebo\_bringup/config/gen\_params.json". 

{% embed url="https://github.com/rudislabs/sim\_gazebo\_bringup/blob/nxp-summer/config/gen\_params.json" %}

This overview will outline each section of the JSON.

1. "setup" -  Sets up the necessary git repositories and file/folder structure.
   1. "autopilot" - This does not need to be changed. It is there for PX4 autopilot simulation, but we are not using that platform for NXP Summer camp yet.
   2. "gazebo" - Sets up Gazebo specific repositories. Car models, track models, libraries, and more.
   3. "ros2" - Sets up ROS2 specific git repositories. These are ROS2 packages.
   4. "system" - This sets up environment variables for your system so that NXP Gazebo knows where to find certain files.
2. "verbose" - This just contains two boolean values to show error logs when running the simulation.
3. "nodes" - This section contains the ROS2 nodes that should be run when the simulation is started. Each node has a few parameters that must be set, and then optional parameters typically go at the end if they exist \(denoted by the "parameters" field\)
4. "world\_params" - This section sets up the simulation world. You can add models to the world using this section, or even change the entire world layout \(the track\). Realtime factor and update rate can also be changed manually here.
5. "models" - This section outlines the car models being placed in the world. For now we only have one car model in the world, but more car models can be added. Sensors can be added to the car here as well.

