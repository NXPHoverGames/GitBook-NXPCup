# S32 Design Studio usage tips

If you finished setting up your car and tested the examples, you might want to expand the car drivers provided to you. Here are some tips about how to use S32 Design Studio for common embedded software development tasks.

### Peripherals tool

The Peipherals tool is where you do the initial setup of all the RTD drivers. Here you can configure everything from pins to communication channels.

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption><p>Peripherals tool interface. The button for accessing it is highlighted in the top right</p></figcaption></figure>

### Using interrupts

To set up an interrupt, you must add it in the **Platform** RTD driver. In the Interrupt Controller tab, add a new entry to the table. In the **Interrupt Name** column you must select the hardware interrupt you want to use. In the **Handler** column you need to put the isr name the driver expects.

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

To find the isr name the driver expects, you must search for it in the RTD driver source code.&#x20;

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption><p>Path to the RTD drivers</p></figcaption></figure>

For example, if you want an interrupt on a PWM channel that is using a FTM hardware instance, you must look in **Ftm\_Pwm\_Ip\_Irq.h**

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption><p>Path to the file Ftm_Pwm_Irq.h</p></figcaption></figure>

Inside the file, search for _**ISR(**_ with any app you want using **Ctrl + f**. In this example you can see the search in Notepad++.

<figure><img src="../.gitbook/assets/image (43).png" alt=""><figcaption><p>Search results are displayed on the bottom</p></figcaption></figure>

Search for the name of the isr that you need and copy it. For example, to setup an interrupt on a rising/falling edge of a PWM signal using FTM instance 1 channel 1, copy the name **FTM\_1\_CH\_0\_CH\_1\_ISR.** Go back to the Platform driver and paste the name in the **Handler** column.

### Setting up pins

### Adding RTD drivers

To add another RTD driver, such as UART, press the green add button next to MCAL

<figure><img src="../.gitbook/assets/image (36).png" alt=""><figcaption><p>List of drivers added in your project</p></figcaption></figure>

In the new window, **select **_**All**_** in the dropdown box at the top.** Click on the driver you need to add to your project and press ok.

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>

### Setting clocks
