---
description: How to write software for the FMU and flash and debug the FMU.
---

# RDDRONE-FMUK66 Development

Most of the tools that are generally used for writing, building and debugging software for **RDDRONE-FMUK66**, are best supported under a Linux operating system. Therefore, it is strongly recommended to either use a native Linux setup, or a virtual machine \(VM\) running Linux on a Windows or MacOS computer. In case you are not able to use a native Ubuntu setup, a virtual machine setup will work just fine. This comes at the cost of speed and flexibility, but should not be a big issue for most developers. In this guide, we will set up a virtual machine, but most instructions would also apply to a native setup.

This section explains setting up software for running a virtual machine, creating such a virtual machine, and installing the required development tools inside it.

We will start with [setting up the VirtualBox software](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/virtual-machine) for creating and running a virtual machine. We will also create the virtual machine, in which we will [install the Ubuntu Linux operating system](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/installing-ubuntu). Inside this virtual machine, the basic [PX4 toolchain will be installed](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/px4-toolchain), which should provide all the tools already to build your own firmware binaries from source.

Finally, you will have the choice to install and setup an integrated development environment \(IDE\), which allows you to edit, build and debug the PX4 firmware. The recommend IDE is [MCUXpresso](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/setting-up-mcuxpresso), but we also provide instructions for setting up the popular [Visual Studio Code](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/setting-up-visual-studio-code).

It is very well possible to install all tools on your main operating system, whether you are using Linux, Windows or MacOS. However, we only provide the instructions for setting up a virtual machine, because this should work well for most users and it is easier to support a single platform. You are free to install the tools onto your main operating system, but please be aware that you might need to figure some things out  using other resources. While these tools are cross platform, it should be noted that the majority of developers use Linux or MacOS. 

