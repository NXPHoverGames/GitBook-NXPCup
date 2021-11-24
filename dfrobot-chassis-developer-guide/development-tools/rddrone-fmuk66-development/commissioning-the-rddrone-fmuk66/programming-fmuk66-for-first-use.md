# Programming FMUK66 for first use

## Disclaimer <a href="disclaimer" id="disclaimer"></a>

{% hint style="warning" %}
Note! - NXP does not officially supply any software for the RDDRONE-FMUK66. Expect that it will be completely blank and unprogrammed upon delivery. Normally you should plan to prepare your own [development environment](https://nxp.gitbook.io/hovergames/developerguide/tools), fork the PX4 Git repository and [compile from source code](https://nxp.gitbook.io/hovergames/developerguide/building-firmware).

However - To quickly get started, you can program a precompiled bootloader and PX4 firmware by following the instructions on this page.
{% endhint %}

## Software setup and debugger adapter board <a href="software-setup-and-debugger-adapter-board" id="software-setup-and-debugger-adapter-board"></a>

The bootloader can only be written to the board using a debugger. The RDDRONE-FMUK66 kit includes a J-Link EDU Mini debugger. To use it, you need to install the J-Link Software Pack. Links are provided on the [downloads](https://nxp.gitbook.io/nxp-cup/downloads-and-links) page.

The debugger can be plugged into the FMU using a small adapter board. This small PCB comes with a 3D printed case that can easily be put together. The J-Link debugger can be connected using an **SWD cable**. The connectors have to be oriented such that the **wires directly go to the side of the board**, as shown in the picture below.

While you do not need it right now, the adapter board also has a 6-pin connector for a **USB-TTL-3V3 cable**, which you can use to access the **system console** of the FMU. The 3D printed case has a small **notch** on one side of the connector. The USB-TTL-3V3 cable needs to be plugged in such that the **black (ground) wire is on the same side as this notch** in the case.

![The debug adapter board. Make sure the cables are plugged in as shown.](https://gblobscdn.gitbook.com/assets%2F-L9GLtb-Tz_XaKbQu-Al%2F-LjUvm956HYbfv-iNoRy%2F-LjUzmng0-ZgqjzSRaAH%2F20190711\_093531.jpg?alt=media\&token=fe19b75f-6eca-4073-b94e-6159c18bf5d6)

## Video tutorial <a href="video-tutorial" id="video-tutorial"></a>

We have created a video walking through the instructions below if you prefer watching a video rather than reading documentation. If you get confused at any time during the video, use the documentation below as a reference!

{% embed url="https://youtu.be/55ViAIU3PTM" %}

## Programming the bootloader <a href="programming-the-bootloader" id="programming-the-bootloader"></a>

RDDRONE-FMUK66 expects a bootloader to be programmed onto the board. We will flash the PX4 bootloader, which can be used from the command line or QGroundcontrol to load new PX4 firmware when powering the board. A precompiled binary of the **bootloader** is available on the [downloads page](https://nxp.gitbook.io/hovergames/downloads#rddrone-fmuk66-px4-bootloader).

{% hint style="info" %}
If the board already has a bootloader programmed, there should be a yellow/orange LED blinking when you first power on the FMU with USB attached. If this is the case, you do not have to program the bootloader again.

The bootloader changes infrequently and changes are often minor. Unless instructed to do so, you don't have to update or rewrite the bootloader.
{% endhint %}

Connect the debugger to the FMU using the 7-pin JST-GH connector from the debug adapter board and plug the USB coming from the debugger into your computer. You should provide power to the FMU using a USB cable. Then start the J-Link Commander program, and follow these steps:

* Enter the `connect` command.
* Enter `?` to bring up a window in which you can select the target device.
* In the `Device` field, enter `MK66FN`, select `MK66FN2M0xxx18` and press `OK`.
* Type `s` to select SWD as the target interface.
* Press `enter` to select the default interface speed (4000 kHz).
* Enter `loadbin "/absolute/path/to/bootloader.bin" 0x0` command to write the bootloader to the board at memory address `0x0`. Change the path to the location of the bootloader binary file.

![Debugging setup. The FMU is powered through the micro USB cable.](https://gblobscdn.gitbook.com/assets%2F-L9GLtb-Tz_XaKbQu-Al%2F-LiHx3w39UP7DixEdxld%2F-LiHx9cCWiyu9kk6mFsx%2F20190626\_103732.jpg?alt=media\&token=054e522c-910a-4c82-a958-c59b87700f70)

## Programming the firmware <a href="programming-the-firmware" id="programming-the-firmware"></a>

{% hint style="info" %}
The bootloader includes a special protocol which allows you to update the firmware over USB instead of the debugger. Once the bootloader is programmed, you can use QGroundControl to upload firmware to the board, as will be explained [later](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/commissioning-the-rddrone-fmuk66/px4-configuration-using-qgroundcontrol/firmware).

However, it is also very easy to load the PX4 firmware in the same way as the bootloader. The instructions below will help you to flash the PX4 firmware using the debugger.
{% endhint %}

The firmware can be programmed to the board with almost the same procedure as the bootloader. You first need to download a firmware binary (.bin file) of the PX4 firmware. We keep up-to-date links to the recommended releases [on our downloads page](https://nxp.gitbook.io/nxp-cup/downloads-and-links), because it is important that you start with the most stable and up-to-date version of the firmware.

To write the firmware, you have to make sure the debugger is still plugged into your computer, and the FMU is still powered. If you did not keep J-Link Commander open after writing the bootloader, you can restart it and follow these steps again:

* Enter the `connect` command.
* Enter `?` to bring up a window in which you can select the target device.
* In the `Device` field, enter `MK66FN`, select `MK66FN2M0xxx18` and press `OK`.
* Type `s` to select SWD as the target interface.
* Press `enter` to select the default interface speed (4000 kHz).

{% hint style="danger" %}
Note the PX4 firmware is installed at an offset in memory after the bootloader, at **address 0x6000**. The bootloader was written to address 0x0.
{% endhint %}

Finally, you can write the firmware to the board using the following command:

* Enter `loadbin "/absolute/path/to/firmware.bin" 0x6000` command to write the firmware to the board at memory address `0x6000`, which is the address at which the bootloader will look to start a program. Change the path to the location of the firmware binary file.

{% hint style="info" %}
A more detailed reference and guide on using the debugger and J-Link software to upload any software to the RDDRONE-FMUK66 board is available as well.
{% endhint %}

