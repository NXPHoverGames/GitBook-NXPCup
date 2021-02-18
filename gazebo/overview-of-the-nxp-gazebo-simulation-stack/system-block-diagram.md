---
description: '[WORK IN PROGRESS'
---

# Gazebo System Software block diagram

## DRAFT

NuttX \(PX4-version\) is an RTOS that runs on the hardware itself. It provides a scheduler, drivers and tools that give the hardware many functions, including things like a terminal window and different types of communications interfaces.

PX4 is a vehicle control software stack that sits on top of NuttX RTOS and provides functions that manage the vehicle dynamics, the complex and precise timing to drive motors and actuators, drivers to get data from sensors like accelerometers, Gyro, magnetometers - also known as an IMU \(Inertial measurement unit\), EKF and Sensor fusion calculations based on the IMU data to determine the direction vector and thrust, 

