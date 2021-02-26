---
description: '[WORK IN PROGRESS]'
---

# Changing the NXP Gazebo track

## Guide

Changing the track in NXP Gazebo is easy. All it takes is one line of code!

First, you must choose what track you want to use. The available tracks are stored in `~/git/nxp_gazebo/worlds`. Once you have chosen the specific track you want to use, navigate to `~/git/nxp_ros2_ws/src/nxp_cup_bringup/launch/nxp_cup_race.launch.py` and change the path on line 15 to the filename of the track you want to use.

For instance, if I wanted to use `nxp_raceway_octagon.world`,  I would go to line 15 of the launch file and change it to:

```text
default_world_path = '/home/{:s}/git/nxp_gazebo/worlds/nxp_raceway_octagon.world'.format(str(getlogin()))
```

## Why is there only two tracks?

We currently only have two tracks to offer in Gazebo. Once we create more tracks, we will add them to the repository and you will be able to pull those tracks down to use in your own simulation.

