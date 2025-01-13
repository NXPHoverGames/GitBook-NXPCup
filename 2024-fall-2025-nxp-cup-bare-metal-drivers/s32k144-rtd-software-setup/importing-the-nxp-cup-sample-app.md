# Importing the NXP Cup sample app

To import the example project, go to File > New > S32DS Project from Example

<figure><img src="../../.gitbook/assets/image (17) (1).png" alt=""><figcaption><p>The button is in the top left corner </p></figcaption></figure>

Inside the window that popped up, go to **S32K1 AUTOSAR 4.4 - R21-11 RTD 2.0.0 > Dio Examples** and choose one of the examples provided for Nxp Cup.

<figure><img src="../../.gitbook/assets/image.png" alt="" width="375"><figcaption><p>Press on the arrow to the left of the folder to find the project</p></figcaption></figure>

To generate the configuration of the drivers, go to Peripherals tab, select Update Code and press ok. **All errors in the Peripherals tool should go away after this step**. This step must be repeated if/when you change the configuration in the Peripherals, Clocks, Pins tools.

<figure><img src="../../.gitbook/assets/image (19) (1).png" alt=""><figcaption><p>The Peripherals tool button is in the top right corner</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (20) (1).png" alt=""><figcaption><p>The Update code button is the top middle</p></figcaption></figure>

## Running the code

To run the code, go back to code view (C/C++ button) and press Debug Configurations under the Debug button menu.

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption><p>Top-right is the C/C++ button; Top Middle is the green Debug button</p></figcaption></figure>

Under GDB PEMicro Interface Debugging, select the one with your project’s name. If there isn’t one, create a new one. Press debug to upload the code.

<figure><img src="../../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>
