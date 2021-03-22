# Updating NXP Gazebo

## Guide

Most of the folders in NXP Gazebo are stored in git repositories. This makes it easy to update to the latest software. To update, you can run the following commands:

```text
$ cd ~/git/nxp_gazebo/ && git pull 
$ cd ~/git/nxp_ros2_ws/src/nxp_cup_bringup/ && git pull 
$ cd ~/git/nxp_ros2_ws/src/nxp_cup_vision/ && git pull 
$ cd ~/git/PX4-Autopilot/ && git pull 
```

## If your PX4-Autopilot repository isn't updating...

If you have an older version of the NXP Gazebo stack, your PX4-Autopilot repository may not update. This is because the repository has been moved to `rudislabs/PX4-Autopilot` from `PX4/PX4-Autopilot` on GitHub. You can change the remote url by running:

```text
$ git remote set-url origin https://github.com/rudislabs/PX4-Autopilot.git
```

and then run the commands above to update.



