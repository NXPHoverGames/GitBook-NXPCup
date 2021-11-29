---
description: This pages describes the known issues due to the DF Robot assembly.
---

# Known Issues

## Mounting of steering axis

The self tapping screws for the mount of the wheels to the steering axis do not fit. Just use other screws which would fit.

{% hint style="warning" %}
If you use non self-tapping screws instead, glue the nut to the screw. Otherwise, the nut will getting lost due to vibration.
{% endhint %}

![](../../.gitbook/assets/steering\_axis\_right\_edit.jpg)

## Motor gear assembly

The golden gears for the motors have different boreholes. It is difficult to fit one of the gears on the motor axis. But with a little force it can be pushed to the right place. The gear wheel should be placed in the correct position once and then not be moved again. The other gear has a borehole which is too big. This gear should be glued to the correct position on the motor axis.&#x20;

![](../../.gitbook/assets/motor\_gear2\_edit.jpg)

{% hint style="warning" %}
**Be careful with the glue!** No glue must get into the gear teeth or the motor.
{% endhint %}

## Coupling has just one hub screw per part

Just use one hub screw per part or buy another two hub screws.

![](../../.gitbook/assets/coupling\_wo\_screw.jpg)

## Mounting of the rear wheels

![](../../.gitbook/assets/rear\_wheel\_edit.jpg)

The installation description which is part of the delivered kit shows to use M3x6 screws to mount the rear wheels to the axis. This screws do not fit. Please use M4x8 screws.

## Servo -  Power connection

The Servo motor needs a power connection, but the FMU itself does not supply any power at the PWM pins and the ESCs do not supply voltage to the PWM pins either. So it is recommended to use an external power connection. You can use an UBEC which will be connected to the last PWM pin as shown in the picture. The ground connection (black) must be connected to the upper pin.

![](../../.gitbook/assets/UBEC\_FMU\_edit.jpg)

In the case that you now have to connect threes devices to the XT60 connector for the FMU power module, it may recommended to use a power distribution board. In principle, any PCB board can be used. The connectors only have to be soldered: All "+" cables must be soldered together and all "-" cables must be connected. A connection between "+" and "-" must be avoided.

Or you can buy a power distribution board:

{% embed url="https://www.banggood.com/30x30-35x35-PCB-ESC-Power-Distribution-Board-For-MINI-Quadcopter-Multicopter-p-984686.html?rmmds=buy&cur_warehouse=CN" %}

The  order of the connections does not matter. But it is important that the ground connections are connected to a "-" and all power connections are connected to "-" . The picture below shows a possible order with one ESC.

![](../../.gitbook/assets/PDB\_edit.jpg)

{% hint style="danger" %}
Be aware! The whole chassis is made of metal and the PDB must be connected in such a way that the connections do not cause a short-circuit with the metal of the chassis. It is recommended to fix the PDB to the chassis with plastic screws and plastic spacer.
{% endhint %}

![](<../../.gitbook/assets/PCB mount\_edit (1).jpg>)

As example you can buy these:

{% embed url="https://www.amazon.com/dp/B07Q8V1MV6/ref=cm_sw_r_cp_awdb_imm_t1_L92bGbYQCZ1A9?_encoding=UTF8&psc=1" %}

{% embed url="https://www.banggood.com/Hobbywing-3A-UBEC-5V-6V-Switch-Mode-BEC-For-RC-Models-p-915037.html?cur_warehouse=USA" %}

{% embed url="https://www.conrad.de/de/p/hobbywing-bec-3a-ubec-bec-spannungsregler-5-5-26-v-2108347.html" %}

You also can use other ESCs which supply power at the PWM pins. As an example the Hobbyking ESC HK3-30A work very fine. You need one ESC per motor.

{% embed url="https://hobbyking.com/en_us/hobbykingr-tm-brushless-car-esc-30a-w-reverse.html" %}

## PWM settings for the motor output

The default settings for the PWM motor output do not work for the ESC supplied. Change the following parameter in QGroundControl:

In the parameter tab of QGroundControl go to "PWM Outputs". Than change&#x20;

* **PWM\_MAIN\_DIS3** to **1485** us
* **PWM\_MAIN\_DIS4** to **1485** us&#x20;
* **PWM\_MAIN\_FAIL3** to **1485** us
* **PWM\_MAIN\_FAIl4** to **1485** us
* **PWM\_MAIN\_MIN3** to **985** us
* **PWM\_MAIN\_MIN4** to **985** us

![](../../.gitbook/assets/QGC\_PWM\_Outputs\_edit\_new\_edit.png)

## Mount of Pixy camera

The Pixy camera does not fit to both L-types mounting plates. Just use one of them. The screws for mounting the camera to the L-type plate are not included to the kit. The best case is to use a M3x12 Nut and M3 screws to fix the camera.&#x20;

![](<../../.gitbook/assets/pixy\_mount\_front (1).jpg>)

![](<../../.gitbook/assets/pixy\_mount\_side (1).jpg>)

![](<../../.gitbook/assets/pixy\_mount\_top (1).jpg>)

## Pixy Cable from the brushless kit is wrongly wired

{% hint style="info" %}
This only applies to the **old** version. If you get the kit **after** October 2020, the cable will work.
{% endhint %}

The delivered Pixy Cable of the brushless kit is wired in the wrong way. On the picture below the original cable without the black cover is shown. Here are the first and the last wires connected. The wires has to be changed in the way the following pictures and text shows.

Solder the cable which was connected to the black wire to the white wire and solder the wire which was connected to the brown wire now to the red wire.

![Wrong connections](<../../.gitbook/assets/20200206\_105028 (1).jpg>)

![Right connections](<../../.gitbook/assets/20200206\_111553 (1).jpg>)

The next picture shows the schematics of the cable. Note that the IDC FC 10p connector is marked with a small triangle on the side where pin 1 is. Now the connections at the JST connector have to be corrected. Connect them in the following way:

| IDC FC 10p Connector (Pixy side) | JST GHR-05V-S (FMU side) |
| -------------------------------- | ------------------------ |
| White                            | Pin 1                    |
| Green                            | Pin 2                    |
| Blue                             | Pin 5                    |
| Red                              | Pin 3                    |

The cables can be removed from the JST connector if the little white nose is pulled up a bit. You can do this with a small slot screwdriver or similar tool. After pushing the right cable in the connector make sure that the nose is returned to its place. Be careful and make sure that you do not broke the white nose. The cable may not fit anymore.

![Schematics of the cable. The connector IDC FC 10p has a schmal triangle where the pin 1 is.](../../.gitbook/assets/Pixy\_connector\_FMU\_edit.jpg)

The corrected cable should be look like following picture shows:

![Numbering of the connector](../../.gitbook/assets/Pixy\_corrected.jpg)

You have to separate the wires to change the connections. When you finish the cable, twist the cables. This reduces disturbances and interferences.
