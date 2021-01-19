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

You can install by using nxp\_desktop.sh shell by downloading the file at [https://github.com/rudislabs/desktop\_installs](https://eur01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fgithub.com%2Frudislabs%2Fdesktop_installs&data=04%7C01%7Ciain.galloway%40nxp.com%7Cd77a0397523140c4dfd408d8905fc0e8%7C686ea1d3bc2b4c6fa92cd99c5c301635%7C0%7C0%7C637418088546900236%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C1000&sdata=kPowsaEv9KksvDmXgfs5MROmtJsYblkL6UzmLwIwiF0%3D&reserved=0)

After downloading the file you may need to make it executable:

change to the directory where nxp\_desktop.sh was downloaded..

`chmod a+x ./nxp_desktop`

It will create some directories including one called git  
`cd ~/git/nxp_ws`

and run:

\(This may take a few minutes\)

`./nxp_cmd config config/nxp_cupcar.rosinstall  
./nxp_cmd update  
./nxp_cmd build`



then load your local variables using:  
  
 `source ~/.bashrc`  
  
To start the simulator with the nxp\_cuprace track   
 `roslaunch nxp_gazebo nxp_cuprace.launch`

