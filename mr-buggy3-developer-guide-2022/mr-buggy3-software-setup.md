# MR-Buggy3 software setup

## Step 1: Programming the FMU

{% hint style="info" %}
We suggest using a desktop or laptop running Ubuntu 20.04 for NXP Cup if you are using the MR-Buggy3. This will allow you to develop, build, and deploy code with ease for both the real car and the Gazebo simulation environment. If you are using another platform, please follow the PX4 developer guide here: [http://docs.px4.io/master/en/dev\_setup/dev\_env.html](http://docs.px4.io/master/en/dev\_setup/dev\_env.html)
{% endhint %}

To program the FMU, you will need to clone two git repositories. On your Ubuntu 20.04 machine, please run the following commands:

```
$ cd ~ && mkdir git && cd git
$ git clone https://github.com/rudislabs/PX4-Autopilot --recursive -b pr-cupcar-v2
```

This will clone the PX4-Autopilot firmware repository to your machine.

In order to flash our board, we need to build the firmware. Before we do so, we need to install the necessary software packages that allow us to build this software. Please run the following command to install the toolchain:

```
$ bash .~/git/PX4-Autopilot/Tools/setup/ubuntu.sh
```

Once this is done, restart your computer. You will now have the build tools necessary for building PX4.

Next, we need to build the PX4 firmware to flash to our FMU. To do this, please change directories to the PX4-Autopilot folder and run the following command:

```
$ cd ~/git/PX4-Autopilot/ && make nxp_fmuk66-v3_default
```

This process will take a while to finish depending on your machine, so feel free to step away for a moment. Once it is done, we can flash our FMU!

### Connecting the FMU to your computer

There are a couple of items that need to be completed before flashing our FMU:

1. Download the bootloader
2. Download and install the J-Link software pack
3. Connect our FMU and J-Link debugging interface to our computer

#### Downloading the bootloader

The FMU requires a bootloader to run. You will be able to flash this using the J-Link debugger. Please follow the instructions here on the HoverGames gitbook:\
[https://nxp.gitbook.io/hovergames/downloads#rddrone-fmuk66-e-px4-bootloader](https://nxp.gitbook.io/hovergames/downloads#rddrone-fmuk66-e-px4-bootloader)

{% embed url="https://nxp.gitbook.io/hovergames/downloads#rddrone-fmuk66-e-px4-bootloader" %}



#### Download and install the J-Link software pack

Please follow the instructions at the J-Link website to install the J-Link software pack for your operating system. A link is provided below:

{% embed url="https://www.segger.com/downloads/jlink" %}
J-Link Software Pack
{% endembed %}

#### Connect our FMU and J-LInk debugging interface to our computer

In your FMU kit, you should have received an orange adapter board that connects the J-Link debugger to the FMU. This adapter board is shown in the image below. Please connect the J-Link debugger to the adapter board like so:

{% hint style="info" %}
You can ignore the USB-TTL-3V3 cable for this step, as it is not needed.
{% endhint %}

![](../.gitbook/assets/20190711\_093531.jpg)

Then, connect the 7-pin JST GH connector to the FMU's "DEBUG" port. You will also need to connect a microUSB cable to the FMU to power it. Once you have connected both of these cables, you should have a setup similar to the image below (minus the USB-TTL-3V3 cable):

![](<../.gitbook/assets/image (56).png>)

Connect the USB cables to your computer and continue with the step.

### Flashing the FMU

First, locate the two files your will need to flash your FMU (the bootloader and the firmware). The bootloader should be in your downloads folder and the firmware should be at the following location:

`~/git/PX4-Autopilot/build/nxp_fmuk66-v3_default/nxp_fmuk66-v3.bin`

We suggest copying these two files to a known location like your desktop or home folder.

Once you have moved these files to a known location, you can open a terminal window and run the following command to start the J-Link debugger software:

```
$ JLinkExe
```

Once JLinkExe starts, it will ask you to connect. Follow the sequence of commands below by typing them in and pressing `Enter` after each:

1. `connect`
2. `MK66FN2M0XXX18`
3. `S`
4. `4000`

You will then be connected to the Cortex-M4 core in the FMU. You can confirm this by checking the output of the J-Link software. It should say something like "Cortex-M4 Identified".

Once you are connected, you can now start loading the bootloader and firmware. To do this, run each of these commands:

```
JLink> loadbin </path/to/bootloader/file.bin> 0x0
JLink> loadbin </path/to/firmware/file.bin> 0x6000
```

It is very important that you get the correct offsets (`0x0`, `0x6000`), as the bootloader uses these to find the firmware on your FMU's flash chip.

#### Congratulations!

Once you have finished flashing your board, you can press the RESET button on the side of the FMU to reboot it. It will now be running PX4-Autopilot!

## Step 2: Installing QGroundControl

QGroundControl is the ground station software that interfaces with PX4. You will need to use QGroundControl in the next steps to configure your MR-Buggy3 for first use.

Please follow the instuctions at the QGroundControl website to install QGroundControl to your machine:

{% embed url="https://docs.qgroundcontrol.com/master/en/getting_started/download_and_install.html" %}

## Step 3: Configure airframe

Open QGroundControl and click the Q at the top left, then select Vehicle Setup. On the left you should see a set of menus. Select the Airframe menu and scroll down until you see the rover icon. Under the rover icon, click the dropdown and select Generic Ground Vehicle. It should look like the screenshot below.

![](<../.gitbook/assets/image (53).png>)

## Step 4: Calibrate sensors

Next, continue to the Sensors menu, and follow the instructions to calibrate the sensors on your Buggy3. Make sure to follow each sensor calibration carefully, and do exactly what it says to do. If the rover "wobbles" while you are calibrating the Gyroscop and Accelerometer, it can make the calibration eventually fail.

## Step 5: Configure radio controls

Next, turn on your FlySky i-6S radio. You will need to make some configuration changes in the radio itself so it can communicate correctly with the FMU.

### Setting the output mode

On your radio controller, navigate to Settings -> System -> Output mode, and make sure it is configured like the image below (PPS and S.BUS selected):

![](<../.gitbook/assets/image (51).png>)

### Configuring channels

Go to Settings -> Aux Channels -> Functions on your radio controller, and set the following channels to their respective settings:

<table><thead><tr><th>Channel</th><th>Switch/Dial</th><th data-hidden></th></tr></thead><tbody><tr><td>5</td><td>SwA</td><td></td></tr><tr><td>6</td><td>SwB</td><td></td></tr><tr><td>7</td><td>SwC</td><td></td></tr><tr><td>8</td><td>SwD</td><td></td></tr><tr><td>9</td><td>VrA</td><td></td></tr><tr><td>10</td><td>VrB</td><td></td></tr></tbody></table>

### Setting up the Radio Controller in QGroundControl

Next, open the Radio menu in QGroundControl. Follow the instructions after selecting "Calibrate" on that screen. This will calibrate the sticks. If you would like to set up flight mode control with the switches on the top of the radio controller, navigate to the Flight Modes tab and configure the switches to your liking.

## Step 6: Configure PWM parameters

In PX4, the default PWM parameters will not work for Buggy3. You will need to go to the Parameters tab and scroll down to "PWM Outputs". Use the search function at the top of the parameters tab to search for the following parameters. Please set their values to the one assigned in the table below.

{% hint style="info" %}
The image below is just an example of the parameters tab. The values set there are outdated. Please use the table below to set the correct values.
{% endhint %}

| Parameter       | Value  |
| --------------- | ------ |
| PWM\_MAIN\_DIS2 | 1500us |
| PWM\_MAIN\_DIS4 | 1500us |
| PWM\_MAIN\_MIN2 | 1300us |
| PWM\_MAIN\_MIN4 | 1000us |
| PWM\_MAIN\_MAX2 | 1700us |
| PWM\_MAIN\_MAX4 | 2000us |

![](<../.gitbook/assets/image (49) (1).png>)

## Step 7: Test!

Test your buggy by manually controlling it using the FlySky i-6S controller.&#x20;

{% hint style="info" %}
Don't forget to ARM your system!\
Depending on how your system is configured, Arming may be required using QGroundcontrol, the PX4-ARMING-BRD, or the GPS Module arming switch.\
There may even bee more than one arming method requred simultaneously

(For example with drones you arm with the GPS first, then use the RC remote sticks pointed toward bottom middle to start the motors)
{% endhint %}



Use QGroundControl to arm the rover.
