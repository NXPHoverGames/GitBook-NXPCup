# Configuring the PixyCam

DRAFT DRAFT DRAFT

{% hint style="danger" %}
This page under contruction. The purpose is to ensure the PixyCAM is correctly configured for line follow mode as used in NXP-CUP. The text below and link to code may not be the best example and needs review. 11/21/2022
{% endhint %}

## Using Pixy2 with PX4

~~A basic port of the Pixy library for Arduino was made for PX4/NuttX. This code allows you to connect the Pixy2 through I2C or SPI to the FMUK66. It provides a simple interface to access the data coming from the Pixy2 in your own PX4 modules.~~

The code is available under the NXP HoverGames GitHub:

{% embed url="https://github.com/NXPHoverGames/PixyCam" %}

The Pixy 2 device has to be configured first. You can find how to set the right Interface [here](https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:porting\_guide). \
And the Pixy 2 has to be in the mode "line tracking ". The instructions can be found [here](https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:line\_tracking).
