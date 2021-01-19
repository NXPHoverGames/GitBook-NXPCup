---
description: >-
  This pages describes how to mount the motors, ESCs and the power module for
  the brushless setup
---

# Brushless: Motors, ESCs and Power Module

## Brushless ESC

The motors must be soldered to the ESCs. The sequences must be observed carefully. Both motors must be connected differently, as they are mounted opposite each other on the chassis and should nevertheless move in the same direction.

#### How to connect \(from left to right, when you are looking to ESC, so that you can read the description\)

**Left moto**r: yellow, red, black

**Right moto**r: red, yellow, black

The power cables have to be soldered to the XT60 connector. Be aware that you have to solder both ESC to **ONE** XT60 connector! Alternatively, you can solder the ESCs to a Power Distribution board and solder the XT60 with some cable to the Power Distribution Board either. \(Detailed description at the [Known issues](https://nxp.gitbook.io/nxp-cup/developer-guide/assembly/dfrobot-chassis/known-issues), similar to the FMU power distribution board\)

{% hint style="warning" %}
Please try to solder as short as you could. The longer the soldering takes, the more solder is drawn into the cable and the cable becomes inflexible and can break more easily.
{% endhint %}

Fix the ESC to the Chassis with a cable tie so that the ESC cannot get in conflict with the external rotors.

![](../../../.gitbook/assets/20191205_104829.jpg)

![](../../../.gitbook/assets/20191205_104838.jpg)

## Power Connection

In the FMU kit is a power module. This can be fixed to the lower side of the upper plate with a cable tie. The male connector will be plugged to the battery later. So is might be good to fix the power connection in a position that you can easily reach the male connector later. The female connector must be plugged to the ESC connector. In the case that you use a Power Distribution board \(PDB\), the power module should be connected to the Power connector of the PDB.

![](../../../.gitbook/assets/powermodule_fmu.jpg)

