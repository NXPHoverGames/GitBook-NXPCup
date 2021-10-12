# Setting up NavQ for use on the NXP Cup Car

{% hint style="warning" %}
This section is not meant for NXP Cup contestants as of now. This is for future developments with NXP Cup.
{% endhint %}

## Setting up the FMU

{% hint style="info" %}
Run this on an Ubuntu 20.04 machine.
{% endhint %}

### Install Fast-DDS

```
$ cd ~
$ mkdir src && cd src
$ git clone --recursive https://github.com/eProsima/Fast-DDS.git -b v2.0.0 FastRTPS-2.0.0
$ cd FastRTPS-2.0.0
$ mkdir build && cd build
$ cmake -DTHIRDPARTY=ON -DSECURITY=ON ..
$ make
$ sudo make install
```

### Install Fast-DDS-Gen

```
$ cd ~/src
$ git clone --recursive https://github.com/eProsima/Fast-DDS-Gen.git -b v1.0.4 Fast-RTPS-Gen
$ cd Fast-RTPS-Gen
$ ./gradlew assemble
$ sudo ./gradlew install
```

### Clone & build PX4-Autopilot from rudislabs repo

```
$ cd ~/src
$ git clone --recursive https://github.com/rudislabs/PX4-Autopilot.git -b pr-cupcar
$ cd PX4-Autopilot
# Add nxpcup to PX4-Autopilot/boards/nxp/fmuk66-v3/rtps.cmake under EXAMPLES #
$ make nxp_fmuk66-v3_rtps
# Flash your FMU using rtps binary #
```

## Setting up NavQ

### Flash NavQ with fresh image

To flash NavQ with a fresh image, follow the instructions on the page linked below:

{% embed url="https://nxp.gitbook.io/8mmnavq/getting-started/quickstart/flash-sd-card-with-linux-image" %}

### Run setup script to install ROS2 Foxy and microRTPS

FTP the zip file linked below to NavQ, then unzip using

{% file src="../.gitbook/assets/navq-install.zip" %}
navq-install
{% endfile %}

```
$ unzip navq-install.zip
```

and then run the script inside using 

```
$ ./navq-install/navq-install.sh
```

### Install ROS2 camera tools

Install ROS2 camera tools so we can publish camera data to the `/image` topic. Use

```
$ sudo apt install ros-foxy-cv-bridge \
ros-foxy-image-tools \
ros-foxy-image-transport \
ros-foxy-image-transport-plugins \
ros-foxy-image-pipeline \
ros-foxy-camera-calibration-parsers \
ros-foxy-camera-info-manager \
ros-foxy-launch-testing-ament-cmake 
```

### Clone and build \`nxp_cup_vision\`

Clone `nxp_cup_vision` and then build it using the commands below

```
$ cd 
$ mkdir ros2src
$ cd ros2src
$ git clone https://github.com/rudislabs/nxp_cup_vision.git
$ colcon build --symlink-install
```

Once that is done, source the setup.bash file

```
$ echo "~/ros2src/install/setup.bash" >> .bashrc
```

You should have everything installed now.

## Running simulated PixyCamera 

### Running cam2image

Spin up the camera publisher by running the command below

```
$ ros2 run image_tools cam2image --ros-args -p device_id:=0 -p width:=640 -p height:=480
```

### Running nxp_tack_vision

Spin up the vision code by running

```
$ ros2 run nxp_cup_vision nxp_track_vision
```

###
