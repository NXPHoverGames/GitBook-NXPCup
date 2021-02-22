---
description: '[WORK IN PROGRESS] NOTE: Add more info about scripts being run - Landon'
---

# Installation of NXP Gazebo

{% hint style="warning" %}
These are draft instructions and may change or be updated. Please check back here regularly.

If you run into issues with this guide, please use the `Contact` section in the sidebar on the left to get help.
{% endhint %}

## Setting up your Ubuntu desktop environment

You can install by using nxp\_desktop.sh shell by downloading the file at

{% embed url="https://github.com/rudislabs/desktop\_installs" %}

You can do so easily by running the following git clone command using the link from the git repo:

![](../.gitbook/assets/screen-shot-2021-02-04-at-4.11.43-pm.png)

```text
$ git clone https://github.com/rudislabs/desktop_installs
```

Now you should see the `desktop_installs` folder in your home folder:

![Expected output for \`git clone\`](../.gitbook/assets/screen-shot-2021-02-04-at-4.13.36-pm.png)

After downloading the file you may need to make it executable. You can do so by entering the `desktop_installs` directory and running a `chmod` command:

```text
$ cd desktop_installs
$ chmod a+x nxp_desktop.sh
$ ls
```

Now you should see that the `nxp_desktop.sh` file is highlighted green. This means that it has executable permissions.

![Expected output for \`chmod\`](../.gitbook/assets/image%20%289%29.png)

Now, we want to run this file to set up our desktop environment. It will ask you for your Ubuntu user password; just type that in when it asks for it. To run the file, run the following command and you should get the expected output:

```text
$ ./nxp_desktop.sh
```

![Expected output for \`./nxp\_desktop.sh\`](../.gitbook/assets/image%20%288%29.png)

You should now see that your background has changed and the command has given you the `All done!` signal. Great! Now let's run the workspace setup to get Gazebo, PX4, and ROS installed.

## Setting up NXP Cup Simulation software

First, we will need to navigate back to our home folder. Inside the home folder, there should be a new folder named `git`. To get there, run the following commands and check that you have the expected output:

```text
$ cd
$ ls
$ cd git/nxp_ws
$ ls
```

![Expected output for changing to \`~/git/nxp\_ws/\` folder](../.gitbook/assets/image%20%284%29.png)

Now, we will need to run the `nxp_cmd` file to set up our software. To start, run the following commands and make sure you get the expected output:

{% hint style="warning" %}
Note: The `update` command will take some time depending on your internet connection.
{% endhint %}

```text
$ ./nxp_cmd config config/nxp_cupcar.rosinstall
$ ./nxp_cmd update
```

![Expected result from \`config\` and \`update\`](../.gitbook/assets/image%20%286%29.png)

Next, you'll want to reboot your virtual machine or PC to allow environment variables to be sourced correctly.

{% hint style="info" %}
You can also log out and log back in to have the same effect.
{% endhint %}

Upon reboot, you will get an error message stating that a `setup.bash` file does not exist. You can simply press `OK` to continue. This error will be fixed after you run the next set of commands. Here is an image of what it looks like:

![Expected error message](../.gitbook/assets/image%20%283%29.png)

Finally, you'll want to navigate back to the `~/git/nxp_ws` folder and run the build command. To do so, run the following commands and make sure you get the expected output:

{% hint style="warning" %}
We recommend that you have at least 6GB of RAM allocated to your VM for the next step. The build will likely fail if you don't have enough memory.
{% endhint %}

{% hint style="info" %}
Note: The next step will take some time depending on the amount of processors and RAM allocated to your machine.
{% endhint %}

```text
$ cd ~/git/nxp_ws
$ ./nxp_cmd build
```

![Expected output for \`build\`](../.gitbook/assets/image%20%287%29.png)

If you get the expected output, you have now finished setup. You can continue to the next section to start the Gazebo simulation!

## Running the Gazebo Simulation

To run the Gazebo simulation, we suggest you first restart your VM or PC and/or log out and log back in. Once you've done so, you can run the following command to start the simulation stack and check to see if you get the expected result:

```text
$ roslaunch nxp_gazebo nxp_cuprace.launch
```

![Expected NXP Gazebo Simulation result](../.gitbook/assets/image%20%285%29.png)

Hooray! You have successfully setup your NXP Cup Gazebo Simulation. For more documentation on how to use the Gazebo simulation, move on to the next section using the buttons below or navigate by using the sidebar on the left.

