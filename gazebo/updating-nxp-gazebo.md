# Updating NXP Gazebo

## Guide

Most of the folders in NXP Gazebo are stored in git repositories. This makes it easy to update to the latest software. To update, copy the script at the bottom of the page and paste it into a file called "update\_nxp_\__gazebo.sh". Then, run the command below:

```text
$ chmod a+x update_nxp_gazebo.sh
```

{% hint style="warning" %}
**NOTE**: This will apply to most NXP Gazebo Summer Camp participants -

If you have made edits to the files in any of these repositories, it is recommended to make a backup of those files before running this. There could be merge conflicts and we will handle those on a case by case basis.
{% endhint %}

```text
#!/bin/bash

cd ~/ros2ws/nxp_gazebo/ && git pull
cd ~/ros2ws/nxp_gazebo/ && git pull
cd ~/ros2ws/gazebo_apriltag/ && git pull
cd ~/ros2ws/src/aim_line_follow_c/ && git pull
cd ~/ros2ws/src/nxp_cup_interfaces/ && git pull
cd ~/ros2ws/src/nxp_cup_vision/ && git pull
cd ~/ros2ws/src/sim_gazebo_bringup && git pull
```





