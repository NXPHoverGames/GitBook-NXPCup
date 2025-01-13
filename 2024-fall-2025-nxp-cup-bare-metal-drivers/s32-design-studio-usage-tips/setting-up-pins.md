# Setting up pins

To configure pins on the S32K144 development board using the S32 Design Studio, follow these steps:

1. **Open the Pins Tool**:

In S32 Design Studio, navigate to the Pins Tool. This tool allows you to select and configure the pins you want to use on the microcontroller. Locate the desired pin in the tool, check the box next to it to choose its signal and enable it for your project.

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption><p>Pins tool interface. The button for accessing it is highlighted in the top right</p></figcaption></figure>

After you check the box the pin will appear in the Routing Details tab where you can set the pin direction, initial value, enable pull up or pull down resistors etc.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

<mark style="color:red;">Note: When selecting a pin by checking its box, you may come across pins reserved for debugging purposes. If you assign one of these pins for another function, it could prevent you from being able to debug your program. You should ignore these pins and use another.</mark>

![](<../../.gitbook/assets/image (6).png>)



2. **Configure the Pins in the Peripheral Tool**:

After selecting the pin in the Pins Tool, switch to the Peripheral Tool. Inside the Peripheral Tool, go to the **Port Driver** section. Here, you will configure the ports for the selected pin. In the Port Driver, find the **PortConfigSet** section.

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Add a new channel to this section. This channel will be associated with the pin you enabled earlier.&#x20;

<figure><img src="../../.gitbook/assets/image (2).png" alt="" width="98"><figcaption></figcaption></figure>

If you want to organize your pins better, you can add them to a container. For example, all the pins related to UART serial communication can be added to the UART container.

We recommend assigning a descriptive name to each pin. The PortPin PCR connects the pin selected in the Pins tool to the RTD PORT driver. You'll need to provide the pin's PCR, which is calculated as follows:

**PCR = (LETTER\_INDEX - 1) \* 32 + PIN\_NUMBER**.

Here, the **LETTER\_INDEX** refers to the position of the port letter in the alphabet (e.g., A = 1, B = 2, etc.).

Example:&#x20;

PA0 = (1 - 1) \* 32 + 0 = 0

PC7 = (3 - 1) \* 32 + 7 = 71&#x20;



Bellow you can see how I activated both UART pins for serial communication.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Now that you’ve activated the pins you want to use, the next step is to configure their respective driver in the Peripherals tool.
