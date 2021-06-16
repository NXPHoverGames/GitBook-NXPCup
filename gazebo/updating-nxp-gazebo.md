# Updating NXP Gazebo

## Guide

Most of the folders in NXP Gazebo are stored in git repositories. This makes it easy to update to the latest software. To update, you can run the following commands:

```text
$ cd ~/ros2ws/nxp_gazebo/ && git pull \
 && cd ~/ros2ws/nxp_gazebo/ && git pull \
 && cd ~/ros2ws/osrf/models/ && git pull \
 && cd ~/ros2ws/gazebo_apriltag/ && git pull \
 && cd ~/ros2ws/src/aim_line_follow/ && git pull \
 && cd ~/ros2ws/src/nxp_cup_interfaces/ && git pull \
 && cd ~/ros2ws/src/nxp_cup_vision/ && git pull \
 && cd ~/ros2ws/src/sim_gazebo_bringup && git pull
```





