# Using interrupts

### Using interrupts

To set up an interrupt, you must add it in the **Platform** RTD driver. In the Interrupt Controller tab, add a new entry to the table. In the **Interrupt Name** column you must select the hardware interrupt you want to use. In the **Handler** column you need to put the isr name the driver expects.

<figure><img src="../../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

To find the isr name the driver expects, you must search for it in the RTD driver source code.&#x20;

<figure><img src="../../.gitbook/assets/image (41).png" alt=""><figcaption><p>Path to the RTD drivers</p></figcaption></figure>

For example, if you want an interrupt on a PWM channel that is using a FTM hardware instance, you must look in **Ftm\_Pwm\_Ip\_Irq.h**

<figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption><p>Path to the file Ftm_Pwm_Irq.h</p></figcaption></figure>

Inside the file, search for _**ISR(**_ with any app you want using **Ctrl + f**. In this example you can see the search in Notepad++.

<figure><img src="../../.gitbook/assets/image (43).png" alt=""><figcaption><p>Search results are displayed on the bottom</p></figcaption></figure>

Search for the name of the isr that you need and copy it. For example, to setup an interrupt on a rising/falling edge of a PWM signal using FTM instance 1 channel 1, copy the name **FTM\_1\_CH\_0\_CH\_1\_ISR.** Go back to the Platform driver and paste the name in the **Handler** column.
