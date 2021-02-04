# Installation of NXP-Gazebo

{% hint style="warning" %}
These are draft instructions and may change or be updated. Please check back here regularly.
{% endhint %}

## Preface

These commands are for an Ubuntu machine or virtual machine running 18.04 or 20.04 or greater.

Linux crash course:  
~/   is how you refer to your home directory in Linux

  
./  is how you refer to "here", or "starting from this directory". \(Since it may not be included  the normal path\)

## Get the installation shell script

You can install by using nxp\_desktop.sh shell by downloading the file at

{% embed url="https://github.com/rudislabs/desktop\_installs" %}

You can do so easily by running the following git clone command using the link from the git repo:

![](../../.gitbook/assets/screen-shot-2021-02-04-at-4.11.43-pm.png)

```text
$ git clone https://github.com/rudislabs/desktop_installs
```

After downloading the file you may need to make it executable:

change to the directory where nxp\_desktop.sh was downloaded..

`chmod a+x ./nxp_desktop`

It will create some directories including one called git  
`cd ~/git/nxp_ws`

and run:

\(This may take a few minutes\)

{% hint style="warning" %}
Before you run ./nxp\_cmd build, you should reboot your VM. This allows any environment variables to be sourced correctly.
{% endhint %}

`./nxp_cmd config config/nxp_cupcar.rosinstall  
./nxp_cmd update  
./nxp_cmd build`



then load your local variables using:  
  
 `source ~/.bashrc`  
  
To start the simulator with the nxp\_cuprace track   
 `roslaunch nxp_gazebo nxp_cuprace.launch`

