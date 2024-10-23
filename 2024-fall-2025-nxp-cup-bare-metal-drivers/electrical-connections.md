# Electrical connections

Note: For some of these steps soldering tools may be required.

### Board pins

<figure><img src="../.gitbook/assets/Connections (2).png" alt=""><figcaption></figcaption></figure>

Refer to [S32K144EVB](https://www.nxp.com/design/design-center/development-boards-and-designs/automotive-development-platforms/s32k-mcu-platforms/s32k144-q100-evaluation-board-for-automotive-general-purpose:S32K144EVB) for more information about the board. Here you will find a picture with all the board pins and pin names. You can also see all pin names on the back of the board. **The board's jumpers are also detailed here, used for selecting power input source (battery or USB).**

### Powering the board

The board can be powered in two ways: through the micro usb connector on the top left, or through the onboard voltage regulator. The voltage regulator is connected to both the LIN pins and the barrel jack connector.

To select between micro usb and onboard regulator, you must move the highlighted jumper accordingly. To power it via usb, put it in the left position. To power it via the onboard regulator, put it in the rightmost position.

<figure><img src="../.gitbook/assets/Jumper.png" alt=""><figcaption><p>Power selection jumper highlighted. Micro usb power is selected</p></figcaption></figure>

For powering the board you will need the following XT60 connector. You can either buy one or make one yourself from two XT60 connectors and two wires/jumpers.&#x20;

<figure><img src="../.gitbook/assets/image (48).png" alt="" width="263"><figcaption><p>XT60 passthrough with dupont adapter </p></figcaption></figure>

You can use double sided tape to secure the battery on the bottom board. **Make sure you can still take it out for charging.**

<figure><img src="../.gitbook/assets/Fotografii selectate (1).jpg" alt=""><figcaption></figcaption></figure>

The red (vcc) and black(gnd) dupont wires will be connected to the LIN header pins, VBAT and GND as you can see in the picture below. **To power the board, make sure the jumper for selecting input power source is in the right position.**

<figure><img src="../.gitbook/assets/Fotografii selectate.jpg" alt=""><figcaption></figcaption></figure>

The LiPo battery goes in the female port of the connector, and the ESC/Hbridge goes in the male port of the connector. Most ESC already have a connector soldered, but for the Hbridge you will need to provide one yourself. Again, you will need an adapter which you can buy or make yourself.

<figure><img src="../.gitbook/assets/image (50).png" alt="" width="213"><figcaption><p>Hbridge power adapter</p></figcaption></figure>

### H Bridge

{% file src="../.gitbook/assets/L298.PDF" %}
H Bridge circuit datasheet
{% endfile %}

Firstly, we will connect the battery adapter and motors.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption><p>Hbridge ports </p></figcaption></figure>

Loosen the screws on the Hbridge ports. Insert the cables from the power adapter in the GND and VMS ports, and screw them in. Insert the cables from the first motor in MOTORA, and the second motor in MOTORB.

Note: the 5V port will be used for powering the servo.

<div>

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="188"><figcaption><p>Motor cables</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_145358715.png" alt="" width="563"><figcaption><p>Motor cables connected</p></figcaption></figure>

</div>

This is how it should look completed:

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="375"><figcaption><p>Final result</p></figcaption></figure>

Next are the connections for controlling the H bridge. Connect them like in the picture. You can also use the picture at the beginning of this page for reference.

<div>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_145521449.png" alt=""><figcaption></figcaption></figure>

</div>

### Servo

Servos have a 3-pin connector for power, pwm and ground. This servo has a brown ground, red power and orange pwm wires. Connect the pwm and ground wires to the board, and the power wire to the H bridge or ESC, depenting on what you are using.

<div>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption><p>Pwm and ground wires connected to the board</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150139855.png" alt=""><figcaption><p>Power wire connected to the H bridge</p></figcaption></figure>

</div>

### ESC

Electronic speed controllers have the same 3-pin connector for power, PWM and ground.

Note: These controllers come in many shapes and sizes, and many do not have any mounting hardware. You can use double-sided tape to mount it to your upper plate in the place of the H bridge.

<figure><img src="../.gitbook/assets/image_2024-09-30_155337397.png" alt="" width="375"><figcaption><p>ESC with connectors for two motors</p></figcaption></figure>

Connect the red power pin of the ESC to the power pin of the servo. The ground wire of the ESC must be connected to both the servo and the development board. You can either solder the ends of three wires together or use a 3-pin male header to connect three jumpers and solder a wire across the exposed ends.

<div>

<figure><img src="../.gitbook/assets/image_2024-09-30_155327069.png" alt=""><figcaption><p>Connecting the three grounds together in the male header with a wire soldered across it</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155219631.png" alt=""><figcaption><p>Two grounds connect the ESC and Servo, the last one will go in the microcontroller.</p></figcaption></figure>

</div>

<div>

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption><p>ESC connections</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155119473.png" alt=""><figcaption><p>Servo connections</p></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/image (25).png" alt="" width="563"><figcaption><p>All connections</p></figcaption></figure>

### Pixy

Official Pixy2 documentation:  [https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:start](https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:start)

The Pixy2 with the I2C interface needs four pins: power, ground, SCL and SDA.  Connect them like in the pictures below.&#x20;

Note: You might need to use longer jumpers, or daisy chain multiple jumpers to reach the desired height with the camera.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (6).jpg" alt="" width="375"><figcaption><p>Daisy chained jumpers</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (1) (4).jpg" alt="" width="375"><figcaption></figcaption></figure>

</div>

Here you can see the pins used on the camera. Make sure you use the **5V pin** and not the **Vin pin** for powering the camera.

<figure><img src="../.gitbook/assets/image_248_2.jpg" alt=""><figcaption><p>Pixy pins documentation</p></figcaption></figure>

<figure><img src="../.gitbook/assets/Fotografii selectate (2) (3).jpg" alt=""><figcaption></figcaption></figure>

### Display

{% file src="../.gitbook/assets/ssd1306_datasheet.pdf" %}
Display driver chip datasheet
{% endfile %}

The display has power, ground, SCL and SDA pins. Connect them like in the pictures below. You can see each pin designation written on the display PCB.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (2).jpg" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (2) (1).jpg" alt=""><figcaption></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/Fotografii selectate (1) (1).jpg" alt=""><figcaption></figcaption></figure>

### **Pixy and display**

Since both components use I2C, they must connect to the same SCL and SDA pins of the microcontroller. You can either solder the ends of three wires together, or use a 3-pin header with a soldered wire across it, like you can see below.&#x20;

<div>

<figure><img src="../.gitbook/assets/shared image.jpg" alt="" width="375"><figcaption><p>The 3-pin header with a soldered wire across it</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_135143963.png" alt="" width="375"><figcaption><p>Jumpers connected to the header</p></figcaption></figure>

</div>

One end goes to the camera, one to the display and one to the microcontroller. The pictures below do not show the power and ground wires so you can see the SCL and SDA wires easier. The power and ground connections are the same ones as seen before.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (1) (5).jpg" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (7).jpg" alt=""><figcaption></figcaption></figure>

</div>

### Linear camera

{% file src="../.gitbook/assets/TSL1401.PDF" %}
Linear camera datasheet
{% endfile %}

Linear camera modules come in many shapes and sizes. For our particular model, the camera is connected through a ribbon to the pin header. You can see the name of each pin in the picture below.

<div>

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption><p>All connections</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150251607.png" alt=""><figcaption><p>Ribbon cable breakout board connections</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150302605.png" alt=""><figcaption><p>Board connections</p></figcaption></figure>

</div>

### Receiver

{% file src="../.gitbook/assets/Notes-on-FlySky-FS-i6.pdf" %}
Receiver manual
{% endfile %}

{% file src="../.gitbook/assets/fsi6s.pdf" %}
Transmitter/RC Remote manual
{% endfile %}

The receiver needs 3 pins: power, ground and PPM. The PPM signal is available on the leftmost column of the receiver.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (3).jpg" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (1) (2).jpg" alt=""><figcaption></figcaption></figure>

</div>

The PPM signal must also be enabled in the remote's settings. On the touchscreen, hold the lock button for a few seconds to **unlock the settings button, and press it**.&#x20;

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (2) (2).jpg" alt=""><figcaption><p>Initial remote screen</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (4).jpg" alt=""><figcaption><p>Screen after holding the 'Lock' button</p></figcaption></figure>

</div>

In the new menu, press on SYS to enter system settings.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (1) (3).jpg" alt=""><figcaption><p>New 'Function' menu</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (4) (1).jpg" alt=""><figcaption><p>'System' or SYS menu</p></figcaption></figure>

</div>

Scroll down to find the 'Output' tab and select it. In the new tab, under Output select PPM insead of PWM. This will change the leftmost data pin of the receiver to output eight channels on one pin with a PPM signal, instead of just one PWM signal assigned to the first channel. The Serial parameter on the right does not matter.

<div>

<figure><img src="../.gitbook/assets/Fotografii selectate (5).jpg" alt=""><figcaption><p>Scrolled down in the 'System' tab to find 'Output'</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/Fotografii selectate (3) (2).jpg" alt=""><figcaption><p>Output mode configured to use PPM</p></figcaption></figure>

</div>
