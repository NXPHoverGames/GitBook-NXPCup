# AprilTag Example Code Overview

## Subscribing to the /apriltag/detections topic

The AprilTag detection node exposes a new topic called `/apriltag/detections`. This topic contains data detailing the ID of the AprilTag, the location within the image, and more. In NXP Gazebo, you will really only need the ID data.

If you want to see the full detail of the AprilTagDetection message, see below:

{% embed url="https://github.com/christianrauch/apriltag\_msgs/blob/master/msg/AprilTagDetection.msg" %}

To subscribe to the /apriltag/detections topic, we need to create a new subscriber. In the updated example code, you will find the following lines:

```text
apriltag_subscription_ = this->create_subscription<apriltag_msgs::msg::AprilTagDetectionArray>(
                              "/apriltag/detections", 10, std::bind(&LineFollower::apriltag_callback,
                              this, std::placeholders::_1));
```

This section of code is similar to the simulated Pixy camera subscription, just adapted to the AprilTagDetectionArray message in the /apriltag/detections topic. You can see within this section of code we passed a new callback function called LineFollower::apriltag\_callback. This function will be run each time an AprilTagDetectionArray is published.

## Using the new callback function

The new LineFollower::apriltag\_callback function will allow you to use the data from the /apriltag/detections topic at your disposal. An example function which prints out the ID of the detected AprilTag is included in the new example code.

```text
  /*
   * NXP SUMMER CAMP PARTICIPANTS:
   * This code just shows you how to retrieve the data from the
   * AprilTag node. You will need to use this data to perform actions
   * with the car within listener_callback.
   */
  void apriltag_callback(apriltag_msgs::msg::AprilTagDetectionArray::SharedPtr msg)
  {
    // Check to see if the detections object is empty. If so, then no detections found.
    if(!msg->detections.empty())
    {
      // Store the 1st detection in an AprilTagDetection object
      apriltag_msgs::msg::AprilTagDetection detection = msg->detections[0];
      // Print the detection ID to the ROS INFO stream
      RCLCPP_INFO(this->get_logger(), "Detection found! ID: %d\n Count: %d\n", detection.id, stop_count);
    }
  }
```

Note that the function looks for the first AprilTag detected. Within NXP Gazebo, only one AprilTag will be shown at any given time, so you won't need to worry about using a detection other than detection 0.

## Questions?

If you have questions, please don't hesitate to ask Landon in the NXP Gazebo Summer Camp Teams channel!

