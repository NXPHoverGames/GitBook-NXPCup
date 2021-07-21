# Basics of ROS and how to write your algorithms in NXP Gazebo

## The Robot Operating System \(ROS\)

### Basics of ROS

ROS is actually not an operating system - it is a software platform for robotics. In the simplest terms, ROS is a set of tools and software that allows users to communicate data between "nodes". Nodes are processes that run within the ROS framework that control subsystems of a robot. Nodes communicate between each other using a Publish/Subscribe protocol \(or a Client/Server protocol, but we are just using Pub/Sub in NXP Gazebo\). ROS "messages" are defined in `.msg` files and loaded into code to be populated and published to a ROS "topic". ROS "topics" are like data ports for certain messages. Nodes can publish data to these topics, or receive data from them by subscribing to them.

Below, you can see a simple GIF that shows the basics of communication between nodes in ROS.

![Credit: https://docs.ros.org/en/foxy/Tutorials/Topics/Understanding-ROS2-Topics.html](https://docs.ros.org/en/foxy/_images/Topic-MultiplePublisherandMultipleSubscriber.gif)

### ROS topics and messages within NXP Gazebo

In NXP Gazebo, the two main topics are `/cupcar0/PixyVector` and `/cupcar0/cmd_vel`. These topics facilitate transfer of a `PixyVector` message and `Twist` message respectively. The `PixyVector` message holds line vector information from the simulated Pixy camera, whereas the `Twist` message contains vector data for linear and angular velocities of the car.

## Where do I start?

For NXP Cup participants, ROS might be a new platform that they haven't used before. In NXP Gazebo, ROS enables the Gazebo simulator and the communication between your self-driving algorithms and the simulated NXP Cup car. 

Thankfully, the team at NXP has set up the simulation environment in a way that keeps the learning curve low. All you need to do is write your algorithm in either C++ or Python and populate two variables to get the car to drive.

To begin writing your code, navigate to `~/ros2ws/src/aim_line_follow_c/src/aim_line_follow_c.cpp` for C++, or `~/ros2ws/src/aim_line_follow/src/aim_line_folow.py` for Python.

![](../../.gitbook/assets/image%20%2844%29.png)

These two files are the source files for your self driving code whether you prefer C++ or Python. Both of them are heavily commented, and you only need to edit the code within the `listener_callback()` function of each.

## How do I write my self-driving algorithm within these nodes?

### Gathering line vector data

In each example node, the function named `listener_callback()` runs whenever the simulated Pixy camera publishes line vector data. This line vector data will be published at a varying rate depending on the performance of your machine, but it will try to keep a consistent 30 frames per second. The line vector data is similar to the pixy camera output - each line has a head and a tail.

```text
------------------------------ PixyVector ROS msg -------------------------------
uint64 timestamp

# Vector 0 head and tail points
uint8 m0_x0    # Tail of vector @ x
uint8 m0_y0    # Tail of vector @ y
uint8 m0_x1    # Head of vector @ x
uint8 m0_y1    # Head of vector @ y

# Vector 1 head and tail points
uint8 m1_x0    # Tail of vector @ x
uint8 m1_y0    # Tail of vector @ y
uint8 m1_x1    # Head of vector @ x
uint8 m1_y1    # Head of vector @ y
```

These values are populated based on how many vectors are found. See the table below for a guide on how to use this data.

| Number of Vectors found | Data population |
| :--- | :--- |
| 0 | All values are set to 0. |
| 1 | The singular vector, no matter what side it is on, will be populated in the Vector 0 points \(m0\_??\) |
| 2 | The left vector will be populated in the Vector 0 points, whereas the right vector will be populated in the Vector 1 points. |

There is a function named `get_num_vectors()` that returns an integer with the number of points found.

### Sending control values to the simulated NXP Cup car

In both the C++ and Python examples, a simple function is included that will publish speed and steer values to the simulated car. 

```text
// C++
void publish_controls(double speed, double steer) {}

# Python
def publish_controls(self, speed, steer):
```

All you need to do is call this function and pass it your speed and steer values!

### Compiling the C++ node

If you're using the C++ node, you will need to recompile the code each time you make a change. To do this, you need to open your terminal and run the following commands:

```text
$ cd ~/ros2ws/
$ colcon build --packages-select aim_line_follow_c --symlink-install
```

