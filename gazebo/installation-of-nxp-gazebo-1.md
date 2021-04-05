# Installation of NXP Gazebo

## Setting up SSH keys

{% hint style="info" %}
To use NXP Gazebo, you will need to have a GitHub account. The installation scripts require a GitHub account with an SSH key.
{% endhint %}

### Creating an SSH key

To create an SSH key, run the following in a terminal:

```text
$ ssh-keygen
```

Follow the prompt. We suggest just pressing enter until you reach the end. It will be easier if you just use the default path for the id\_rsa file and if you go without a passphrase \(though you're welcome to use one!\). You should get the output below. Note that the RSA key is not shown here for security reasons:

![](../.gitbook/assets/image%20%2834%29.png)

Next, you'll want to install `xclip`. This program will allow you to copy the contents of the id\_rsa.pub file to your clipboard so you can paste it into GitHub. To install `xclip`, run the following command:

```text
$ sudo apt install xclip git
```

Once you've installed xclip, you need to copy the id\_rsa.pub file to your clipboard. To do so, run the following command:

```text
$ xclip -sel clip < ~/.ssh/id_rsa.pub
```

### Adding your SSH key to GitHub

Now, log into your GitHub account and paste your SSH key. The SSH key field is located in your account settings under "SSH and GPG keys". Add a new SSH key by pressing "New SSH key" and pasting your SSH key in the box. Make sure to give it a name!

![Black Box added for security](../.gitbook/assets/image%20%2836%29.png)

Once you've done this, you're ready to begin installation.

## Installing ROS2

To run NXP Gazebo, you must have ROS2 installed. This is an easy process - just run the following script:

{% file src="../.gitbook/assets/foxy\_install.sh" caption="foxy\_install.sh" %}

{% hint style="info" %}
You may need to run `chmod a+x foxy_install.sh` to make the script executable.
{% endhint %}

And then source ros2 by running the following commands:

```text
$ echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```

## Installing RTPS

In order to transfer simulated Pixy camera data from ROS2 to simulated PX4, we need to install some software. We are following the guide at the link below, but we will go over the commands in detail here.

{% embed url="https://docs.px4.io/master/en/dev\_setup/fast-dds-installation.html" %}

#### Installing Fast-RTPS \(DDS\)

Clone the project from Github:

```text
$ git clone --recursive https://github.com/eProsima/Fast-DDS.git -b v2.0.0 ~/FastDDS-2.0.0
$ cd ~/FastDDS-2.0.0
$ mkdir build && cd build
```

You should get the expected output from these commands shown below:

![](../.gitbook/assets/image%20%2831%29.png)

Next, we will run some commands to build and install Fast-DDS. Run the following commands:

```text
$ cmake -DTHIRDPARTY=ON -DSECURITY=ON ..
$ make -j$(nproc --all)
$ sudo make install
```

You should get a message stating `[100%] Built target fastrtps` once `make -j$(nproc --all)` is finished, and you should get the expected output shown below after you run `sudo make install`:

![](../.gitbook/assets/image%20%2819%29.png)

#### Installing Fast-RTPS-Gen

Next, we will install Fast-RTPS-Gen. To do so, run the following commands and make sure you get the expected output:

```text
$ git clone --recursive https://github.com/eProsima/Fast-DDS-Gen.git -b v1.0.4 ~/Fast-RTPS-Gen \
    && cd ~/Fast-RTPS-Gen \
    && ./gradlew assemble \
    && sudo ./gradlew install
```

![](../.gitbook/assets/image%20%2829%29.png)

If you got the expected output, great! We will move on to building our ROS2 workspace.

## Installing NXP Gazebo

### Cloning and running sim\_gazebo\_bringup

Installing NXP Gazebo has become much easier over time. With this new install process, you'll be up and running with NXP Gazebo in record time!

First, we need to create a ROS2 workspace directory to store the installation files. Go to your home folder and create a new folder called "ros2ws", and a folder inside of that called "src":

```text
$ cd ~
$ mkdir -p ros2ws/src && cd ros2ws/src
```

Once you are in the directory `~/ros2ws/src`, it's time to clone the bringup repo. The bringup repo contains code that sets up the workspace for you automatically. To clone it, run the following command:

```text
$ git clone git@github.com:rudislabs/sim_gazebo_bringup.git -b nxp
```

When git prompts you to continue connecting with your RSA fingerprint, type yes:

![](../.gitbook/assets/image%20%2835%29.png)

Next, we are going to run `sim_gazebo_bringup`. To do this, run the following commands:

```text
$ cd ~/ros2ws
$ colcon build --packages-select sim_gazebo_bringup --symlink-install
$ echo "source /home/$USER/ros2ws/install/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```

Now that we have the bringup package set up, we can start installing all of the NXP Gazebo packages. Run the following command:

```text
$ ros2 launch sim_gazebo_bringup sim_gazebo.launch.py
```



