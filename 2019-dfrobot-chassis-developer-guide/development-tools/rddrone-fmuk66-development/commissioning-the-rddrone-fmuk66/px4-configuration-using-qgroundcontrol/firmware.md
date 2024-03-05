---
description: How to upload firmware onto the RDDRONE-FMUK66 using QGroundControl.
---

# Firmware

When a compatible bootloader is present on the target device, QGroundControl can update the firmware on it. You can use this feature to update the PX4 firmware on the RDDRONE-FMUK66, but also to update firmware on telemetry radio modules.‌

The QGroundControl user guide provides a clear description of the firmware uploading process. Please have a look at their documentation:

{% embed url="https://docs.qgroundcontrol.com/en/SetupView/Firmware.html" %}

## Uploading PX4 firmware using QGroundControl <a href="#uploading-px4-firmware-using-qgroundcontrol" id="uploading-px4-firmware-using-qgroundcontrol"></a>

It is recommended to use PX4 on the RDDRONE-FMUK66. It's an opensource flight stack containing all the software necessary to get your drone into the air. PX4 is constantly being updated with stability improvements and new features. It is recommended to always run the latest (stable) firmware on your FMU, as constant updates will make your drone fly more stable, add exciting new features and open up more possibilities for using different sensor types. In the Firmware screen you can upload a new version of PX4.

{% hint style="info" %}
You probably already [programmed the PX4 firmware after you programmed the bootloader](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/commissioning-the-rddrone-fmuk66/programming-fmuk66-for-first-use)! In that case you do not have to program firmware again. However, you can use this feature to upgrade to newer firmware versions when they become available.‌
{% endhint %}

QGroundControl will ask you to plug in your FMU using a USB cable. It might also ask you to first unplug it again, because it needs to enter the bootloader before it can upload firmware. A popup will appear that asks you which flight stack you want to use. We will use the PX4 flight stack. You can choose between the standard (stable) version and test/development versions, or a custom firmware binary. It is **recommended to use the stable version**, for now.You can choose between the stable version (recommended) and test / development versions.‌

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-Lc6LXsNdqzsJAtrhD0K%2F-Lc6M19M9aY-Qs9gb1xx%2Ffirmwareupload.jpg?alt=media\&token=63494386-19a9-429b-b036-4359a5c1916d)

It is also possible to build the firmware yourself (or [download binary files from the PX4 Continuous Integration server](http://ci.px4.io/job/PX4\_misc/job/Firmware-compile/job/master/lastSuccessfulBuild/artifact/build/nxp\_fmuk66-v3\_default/)), and upload it through the custom firmware option. Instructions for building your own firmware binaries from source are available in the developer guide:

{% embed url="https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/commissioning-the-rddrone-fmuk66/building-px4-firmware" %}

## Updating the telemetry radio firmware <a href="#updating-the-telemetry-radio-firmware" id="updating-the-telemetry-radio-firmware"></a>

It is recommended to also update the firmware on your telemetry radios. Simply go to the Firmware tab in QGroundControl and plug in your radio using a USB cable. Make sure you only have the radio plugged in to your laptop, no FMU. QGC should automatically detect the radio and start the firmware upgrade process. If you get any errors during this process, starting over usually works.‌

You have to do this for both radios! If you don't, you might not be able to establish a connection. Make sure the radio on the drone is not connected to the FMU (take out the JST-GH connector) and connect it with a USB cable to your computer, just like the other radio.Telemetry radio firmware upgrade.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz\_XaKbQu-Al%2F-Lc6LXsNdqzsJAtrhD0K%2F-Lc6Md0u8AtWCbDRb5sD%2Fimage.png?alt=media\&token=6eb21d86-191d-4023-b3e4-5b90acea374e)
