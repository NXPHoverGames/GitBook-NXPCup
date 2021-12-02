# \[NOTICE] Update - 12.2.2021

## Changes needed

On 12.2.2021, some updates were made to the general parameters file in NXP Gazebo. NXP has had to remove some forked repositories from the NXPHoverGames GitHub account due to licensing issues.

Some repositories are now being pulled from their original owner's repository. Some changes will need to be made to these repos before the simulation can be installed successfully.

## Change 1

In \~/ros2ws/models/gazebo\_apriltag, you will need to change the size of each apriltag model. To do this, go to \~/ros2ws/models/gazebo\_apriltag/models/. In each model folder, there is a model.sdf file. The model.sdf file needs to be changes to adjust the size.&#x20;

At this line:

{% embed url="https://github.com/koide3/gazebo_apriltag/blob/872685ad46cde1aa87e31278e0466d3887cb83a4/models/Apriltag36_11_00000/model.sdf#L9" %}

Change the size parameters to 0.33 0.33 0.01.

## Change 2

In \~/ros2ws/src/apriltag\_ros, change the CMakeLists.txt file at this line:

{% embed url="https://github.com/christianrauch/apriltag_ros/blob/245c8cb57e92c24b8323fe35f456b20d2592a2d0/CMakeLists.txt#L26" %}

You will need to remove the ::apriltag so that it says:

```
target_link_libraries(AprilTagNode apriltag)
```

## Future updates

Future updates will be posted on this page. The date will be updated when new updates are released.
