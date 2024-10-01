# Setting clocks

While configuring your peripherals, you may need to adjust the clock settings. For instance, a clock speed of 48 MHz might be too fast for UART communication. Let's now discuss clock configurations.

The diagram below illustrates the clock tree, showing how all clocks are distributed.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption><p>Clocks tool interface. The button for accessing it is highlighted in the top right</p></figcaption></figure>

In the Peripheral Clock View tab, each peripheral is assigned a specific clock. These clocks will be utilized in subsequent driver configurations through the Microcontroller Unit (MCU) RTD driver.

<figure><img src="../../.gitbook/assets/image (28).png" alt="" width="482"><figcaption></figcaption></figure>

In the Peripherals we go to MCU -> McuModuleConfiguration -> McuClockSettingConfig -> McuClockReferencePoint. Here you can see all the references to the clocks we are using in the project.&#x20;

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

The last one (Lpuart1ClockReferencePoint) is used in the UART configuration we've talked about before.

<figure><img src="../../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

For example let's say that we want to use the clock of LPUART2, another hardware channel for the UART module.&#x20;

We go to McuClockReferencePoint and add a new reference. We give it a suggestive name like "Lpuart2ClockReferencePoint" and choose the pheripheral clock,  "LPUART2\_CLK".

<mark style="color:red;">Note : This example is for demonstration purposes only, and the LPUART1 peripheral should use its own clock.</mark>

<figure><img src="../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

After this if we go back to the UART interface we can find the new clock reference.&#x20;

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

