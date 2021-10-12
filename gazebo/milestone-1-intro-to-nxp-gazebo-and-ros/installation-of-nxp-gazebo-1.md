# Installation of NXP Gazebo

## Setting up SSH keys

{% hint style="info" %}
To use NXP Gazebo, you will need to have a GitHub account. The installation scripts require a GitHub account with an SSH key.
{% endhint %}

### Creating an SSH key

To create an SSH key, run the following in a terminal:

```
$ ssh-keygen
```

Follow the prompt. We suggest just pressing enter until you reach the end. It will be easier if you just use the default path for the id_rsa file and if you go without a passphrase (though you're welcome to use one!). You should get the output below. Note that the RSA key is not shown here for security reasons:

![](<../../.gitbook/assets/image (35).png>)

Next, you'll want to install `xclip`. This program will allow you to copy the contents of the id_rsa.pub file to your clipboard so you can paste it into GitHub. To install `xclip`, run the following command:

```
$ sudo apt install xclip git
```

Once you've installed xclip, you need to copy the id_rsa.pub file to your clipboard. To do so, run the following command:

```
$ xclip -sel clip < ~/.ssh/id_rsa.pub
```

### Adding your SSH key to GitHub

Now, log into your GitHub account and paste your SSH key. The SSH key field is located in your account settings under "SSH and GPG keys". Add a new SSH key by pressing "New SSH key" and pasting your SSH key in the box. Make sure to give it a name!

![Black Box added for security](<../../.gitbook/assets/image (36).png>)

Once you've done this, you're ready to begin installation.

## Installing ROS2

To run NXP Gazebo, you must have ROS2 installed. This is an easy process - just run the following script:

{% file src="../../.gitbook/assets/foxy_install_nxp_summer (2).sh" %}
NXP Gazebo Install Script
{% endfile %}

You can run it by using the following commands:

```
$ sudo apt install curl
$ cd ~/Downloads
$ chmod a+x foxy_install_nxp_summer.sh
$ ./foxy_install_nxp_summer.sh
```

And then source ROS2 by running the following command:

```
$ source ~/.bashrc
```

## Installing NXP Gazebo

### Cloning and running sim_gazebo_bringup

Installing NXP Gazebo has become much easier over time. With this new install process, you'll be up and running with NXP Gazebo in record time!

First, we need to create a ROS2 workspace directory to store the installation files. Go to your home folder and create a new folder called "ros2ws", and a folder inside of that called "src":

```
$ cd ~
$ mkdir -p ros2ws/src && cd ros2ws/src
```

Once you are in the directory `~/ros2ws/src`, it's time to clone the bringup repo. The bringup repo contains code that sets up the workspace for you automatically. To clone it, run the following command:

```
$ git clone git@github.com:rudislabs/sim_gazebo_bringup.git -b nxp-summer
```

When git prompts you to continue connecting with your RSA fingerprint, type yes:

![](<../../.gitbook/assets/image (37).png>)

Next, we are going to run `sim_gazebo_bringup`. To do this, run the following commands:

```
$ cd ~/ros2ws
$ colcon build --packages-select sim_gazebo_bringup --symlink-install
$ echo "source /home/$USER/ros2ws/install/setup.bash" >> ~/.bashrc
$ source ~/.bashrc
```

Now that we have the bringup package set up, we can start installing all of the NXP Gazebo packages. Run the following command:

```
$ ros2 launch sim_gazebo_bringup sim_gazebo.launch.py
```

## You're finished installing NXP Gazebo!

![](https://thumbs.gfycat.com/CheerySizzlingGuillemot-mobile.mp4)

Now that you have successfully installed NXP Gazebo, you can return to the Milestone 1 page. Use the link below to do so.

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}
