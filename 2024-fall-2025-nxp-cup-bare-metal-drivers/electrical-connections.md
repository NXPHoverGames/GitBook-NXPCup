# Electrical connections

Note: For some of these steps soldering tools may be required.

<figure><img src="../.gitbook/assets/Connections.png" alt=""><figcaption></figcaption></figure>

Refer to [Getting Started with the S32K144EVB | NXP Semiconductors](https://www.nxp.com/document/guide/getting-started-with-the-s32k144evb:NGS-S32K144EVB) for more information about the board. Here you will find a picture with all the board pins and pin names. You can also see all pin names on the back of the board. **The board's jumpers are also detailed here, used for selecting power input source (battery or USB).**

## Powering the board

For powering the board you will need the following xt60 connector. You can either buy one or make one yourself from two XT60 connectors. The red (vcc) and black(gnd) dupont wires will be connected to the LIN header pins, VBAT and GND as you can see in the picture below.

<div>

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption><p>XT60 passthrough with dupont adapter </p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption><p>powering the S32K144</p></figcaption></figure>

</div>

The LiPo battery goes in the female port of the connector, and the ESC/Hbridge goes in the male port of the connector. Most ESC already have a connector soldered, but for the Hbridge you will need to provide one yourself. Again, you will need an adapter which you can buy or make yourself.

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption><p>Hbridge power adapter</p></figcaption></figure>

### I2c connections

The OLED display and the Pixy2 camera share the same I2c channel. You must connect all SCL pins together, then do the same for SDA. The picture below shows one way of doing it. This must be done twice, once for the SCL pins and once for the SDA pins.

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption><p>I2c connection. Purple wire goes to K144, green to display and blue to camera.</p></figcaption></figure>

## Board connections

<figure><img src="../.gitbook/assets/K144 Connections.png" alt=""><figcaption><p>Placeholder for photos of connections</p></figcaption></figure>

### Servo

<div>

<figure><img src="../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150139855.png" alt=""><figcaption></figcaption></figure>

</div>

### ESC

<div>

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155119473.png" alt=""><figcaption></figcaption></figure>

</div>

<div>

<figure><img src="../.gitbook/assets/image (25).png" alt="" width="563"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155219631.png" alt="" width="188"><figcaption></figcaption></figure>

</div>

<div>

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155327069.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_155337397.png" alt=""><figcaption></figcaption></figure>

</div>

### H Bridge

{% file src="../.gitbook/assets/L298.PDF" %}
H Bridge circuit datasheet
{% endfile %}

<div>

<figure><img src="../.gitbook/assets/image (17).png" alt="" width="563"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_145244727.png" alt="" width="188"><figcaption></figcaption></figure>

</div>

<div>

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="188"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_145358715.png" alt="" width="563"><figcaption></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="375"><figcaption></figcaption></figure>

<div>

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_145521449.png" alt=""><figcaption></figcaption></figure>

</div>

### Pixy

[https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:start](https://docs.pixycam.com/wiki/doku.php?id=wiki:v2:start)

<div>

<figure><img src="../.gitbook/assets/image_2024-09-30_132918992.png" alt="" width="563"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_133047906.png" alt="" width="188"><figcaption></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/image (12).png" alt="" width="375"><figcaption><p>Pixy connections</p></figcaption></figure>

**Connecting both pixy camera and the display**

<div>

<figure><img src="../.gitbook/assets/image (15).png" alt="" width="375"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_135031668.png" alt="" width="375"><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_135052321.png" alt="" width="375"><figcaption></figcaption></figure>

</div>

<div>

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_135143963.png" alt=""><figcaption></figcaption></figure>

</div>

Linear camera

{% file src="../.gitbook/assets/TSL1401.PDF" %}
Linear camera datasheet
{% endfile %}

<div>

<figure><img src="../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150251607.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_150302605.png" alt=""><figcaption></figcaption></figure>

</div>

### Display

{% file src="../.gitbook/assets/ssd1306_datasheet.pdf" %}
Display driver chip datasheet
{% endfile %}

<div>

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../.gitbook/assets/image_2024-09-30_132733662.png" alt=""><figcaption></figcaption></figure>

</div>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption><p>Display connections</p></figcaption></figure>

### Receiver

{% file src="../.gitbook/assets/Notes-on-FlySky-FS-i6.pdf" %}
Receiver manual
{% endfile %}

{% file src="../.gitbook/assets/fsi6s.pdf" %}
Transmitter/RC Remote manual
{% endfile %}

