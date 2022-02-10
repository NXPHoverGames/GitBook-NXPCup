# Step 11: Wiring the Buggy3

## Task 1: Install FMU power module

Gather the FMU power module:

![](../../.gitbook/assets/IMG\_6058.JPEG)

Plug the power module into the PDB. Route the 6-pin power connector to the top PCB and plug into the FMU POWER port.

You may wish to zip tie the power module to the underside of the PCB

![](../../.gitbook/assets/IMG\_6059.JPEG)

![](../../.gitbook/assets/IMG\_6060.JPEG)

![](../../.gitbook/assets/IMG\_6061.JPEG)

## Note regarding Buggy 3 Battery

The Buggy3 can use a 2S or 3S battery in the range of 1000 - 5000mAh. Carefully check which ones will fit in the space available. A 3S battery may be preferable in in the future depending on what additional companion computers are added (for example NavQPlus.)\
\
The battery should have an XT60 plug end and not the T or DEANS style end.\
An XT60 may be soldered in place (carefully - you must be extra careful to never short the battery pins for risk of fire/explosion!) or an adapter from T/Deans to XT60 may be used.\
&#x20;

![DEANS T  Male connector to XT60 Female](<../../.gitbook/assets/image (49).png>)

![Battery needs to fit in this space on the Buggy](<../../.gitbook/assets/image (51) (1).png>)

### Servo and ESC PWM connections

You will also need to connect the two PWM wires from the servo/ESC. The servo PWM goes in slot 2, whereas the ESC goes in slot 4.

{% hint style="warning" %}
Make sure that the GND wire (brown) goes on top. In the picture below, the cable in PWM slot 4 is INCORRECT! Slot 2 is correct.
{% endhint %}

![](../../.gitbook/assets/IMG\_6057.JPEG)
