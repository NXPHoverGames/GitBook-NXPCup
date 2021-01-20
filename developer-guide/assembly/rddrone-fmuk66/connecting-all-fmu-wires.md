---
description: This page provides an overview of how to connect all wires to the FMU.
---

# Connecting all FMU wires

## Connector pinout <a id="connector-pinout"></a>

We are almost ready. We only need to connect the wires to the right connectors on the FMU. A diagram showing all port locations is available below. [More indepth information](https://nxp.gitbook.io/nxp-cup/hardware-reference/connectors-and-pinout) is also available in the technical reference section. Port locations on the RDDRONE-FMUK66 Rev. C.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-L9GLtb-Tz_XaKbQu-Al%2F-Lb4JCAYBfGv_1_7x9Eo%2F-Lb4JfRjq6gAyj8_67st%2Fimage.png?alt=media&token=8574fcd2-3c55-443f-b0f2-8abe30c6f687)

For the Rover setup the connections shown in the picture below are needed.

{% hint style="danger" %}
One part in this image is missing. In order to control the steering servo you will need an UBEC/BEC to power the +5V rail on the FMU. The FMU does not provide this power by default.

If you do not have an UBEC, the servo will not move. The second image below shows where the UBEC needs to be connected.
{% endhint %}

![](../../../.gitbook/assets/block_diagram_fmu.jpg)

## Servorail

![Pinout of the servo rail.](../../../.gitbook/assets/servo_pinout.png)

| Kind of motor | PWM output |
| :--- | :--- |
| Servo | 2 |
| Motor left | 3 |
| Motor right | 4 |
| UBEC | BEC \(Pin 7\) |



