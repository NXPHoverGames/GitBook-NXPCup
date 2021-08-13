# Detecting AprilTags within simulation

## What's an AprilTag?

An AprilTag is sort of like a QR code, but specifically for robotics. Because our cell phones typically have high resolution cameras, QR codes are quite high resolution. In robotics, camera resolutions are commonly quite low \(think 320x240\). AprilTags are a type of QR code specifically for low resolution cameras within the robotics space.

## Why are we using them?

In NXP Gazebo, we use AprilTags to allow participants to detect objects within the simulation without actually writing computer vision code. Each AprilTag has an ID that will be detected by the included AprilTag detection node. All participants have to do is subscribe to the `/apriltag/detections` ROS topic and check to see if an AprilTag has been detected!

## How do I subscribe to the AprilTag detections topic?

We have updated NXP Gazebo's example code to include a section about subscribing to AprilTags. You can find this example code within the "aim\_line_\__follow\_c.cpp" file. To update your NXP Gazebo, follow the page below:

{% page-ref page="../updating-nxp-gazebo.md" %}



