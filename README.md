# Welcome to NXP Cup

{% hint style="success" %}
Also take a look at some of our other Gitbooks:

* [HoverGames](https://app.gitbook.com/o/-L9GLsni4p7csCR7QCJ8/s/-L9GLtb-Tz_XaKbQu-Al/)
* [NavQPlus (NavQ+) Companion Computer](https://nxp.gitbook.io/8mpnavq/)
* [UCANS32K1 ](https://nxp.gitbook.io/ucans32k146/) CAN-FD / UAVCAN node
* [MR-B3RB](https://app.gitbook.com/o/-L9GLsni4p7csCR7QCJ8/s/U93yDWZcgjXGgsC1Duqv/) Buggy3 Rev B - Autonomous robot car platform


{% endhint %}



### This gitbook can be found at: [https://nxp.gitbook.io/nxp-cup/](https://nxp.gitbook.io/nxp-cup/)

## Welcome to NXP Cup

This Gitbook helps you quick start into the NXP CUP. It contains information on hardware i.e. recommendations, documentation and assembly support. And Software like basic source code and commands.

### From 2024 new options are available:

**Hardware:** You can build your own 3D printed chassis using the provided reference 3D models, or go in and modify them using the provided .STEP files to bring improvements to the design.&#x20;

**Software:** You can write embedded C code using RTD drivers on an S32 MCU. We also provide software support in the form of example codes and documentation for all basic car components.&#x20;

{% hint style="info" %}
You are allowed to compete with the older kit variants too.
{% endhint %}

### Previous years' kit variants are listed below:

#### DFRobot kit:

By default there are [two car chassis](https://community.nxp.com/servlet/JiveServlet/download/1091-27-456210/NXPCUP_Car+Introduction.pdf) configurations by **DFRobot**. These chassis support **brushed** AND **brushless motors**.&#x20;

Moreover there are two new MCUs. First, a board developed entirely for this competition - the "**ARC-Board**" also named "Micro E Board". This board was developed by students and professors of the "Haute-Ecole Arc" in Switzerland and is finally available for every participant. It supports brushed motors and a camera communicating via SPI. The Second board is the [**RDDRONE-FMUK66**](https://www.nxp.com/applications/solutions/industrial/unmanned-aerial-vehicles-uavs/uavs-drones-and-rovers/rddrone-fmuk66-px4-robotic-drone-fmu-reference-design:RDDRONE-FMUK66?\&tid=vanRDDRONE-FMUK66) which is also a part of the [Hovergames drone](https://nxp.gitbook.io/hovergames/). NXP CUP proofs that this particular flight controller is ready to steer rovers too!\
Finally we introduce an intelligent camera into the Cup, the **Pixy 2 camera**. This camera has its own MCU and does line tracking or colored block detection by itself. The Pixy 2 can communicate via I2C, SPI and UART.

All these components and configurations are described in this documentation. The default setup is the DFRobot chassis with brushed motors, the Micro E board and the Pixy 2 OR DFRobot chassis with brushless motors, RDDRONE-FMUK66 and Pixy 2. You pick!

Students have the option of using setups from the past seasons or other NXP MCU boards. But these are not supported in this documentation.

[![Creative Commons License](https://i.creativecommons.org/l/by/4.0/88x31.png)](http://creativecommons.org/licenses/by/4.0/)\
This work is licensed under a [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0/).
