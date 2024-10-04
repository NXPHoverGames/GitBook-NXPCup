# Kit components

## Choosing your components

Below is a list of the main components. We provide software support for two types of motor controllers, an I2c display, a receiver, servomotors and two types of cameras, allowing you to choose whichever one you want.

The main components of the car are:

* Camera
* Motor driver
* Servo
* K144 Development board
* Two brushed DC motors
* Battery

The optional components of the car are:

* Display
* Receiver

### Camera

#### Pixy 2

<figure><img src="../.gitbook/assets/image (75).png" alt="" width="375"><figcaption><p>Pixy 2 camera</p></figcaption></figure>

The Pixy 2 camera is the **tried-and-tested** camera for NXP Cup contests. It has an integrated processor designed for image processing tasks such as line recognition. Since it provides you with all the lines/vectors it sees, you **do not need to write your own line detection algorithm.**

#### Linear CCD camera

<figure><img src="../.gitbook/assets/image (76).png" alt="" width="237"><figcaption><p>TSL1401 Linear CCD camera</p></figcaption></figure>

Linear CCD cameras are **cheaper** and can **perform image acquisition much faster** than a regular camera. This camera contains a TSL1401 integrated circuit and provides you with the light values of 128 horizontal pixels. Unlike the Pixy 2 camera, you will **have to write your own line detection algorithm**.

### Motor controller

#### Electronic Speed Controller

<figure><img src="../.gitbook/assets/image (77).png" alt="" width="375"><figcaption><p>Brushed ESC for one motor</p></figcaption></figure>

Electronic Speed Controllers, while **more expensive**, are better suited for **handling higher loads,** like that of larger motors, or motors without reductors. Some ESC models are also capable of **actively braking**.

Note: Some models of ESC have two pairs of motor wires, suited for spinning two motors at once, while others only have one pair. **You can either get one ESC that has two pairs of motor wires, or two ESCs that have one pair of motor wires, allowing individual motor control.**

#### H-Bridge (L298N)

<figure><img src="../.gitbook/assets/image (80).png" alt=""><figcaption><p>L298N on an expansion board</p></figcaption></figure>

For **smaller motors** and **motors with reductors**, this is a **good, low-cost** option. It is best suited for driving **loads that do not exceed 2A.** It also allows individual control for each motor.

### Motors

<figure><img src="../.gitbook/assets/image (81).png" alt="" width="231"><figcaption><p>GA12-N20 motor with reductor</p></figcaption></figure>

We recommend starting with the **GA12-N20** brushed motor-reductor combo. They **draw little current, extending battery life** and their slower speed is **well suited for safely testing your car**. Once you feel confident enough in your car, you can upgrade to some larger motors for improved speed and design your own reductor for improved torque.

Note: These motor-reductor combos come in a variety of reduction ratios, however we **do not recommend ratios larger than 30:1**, as they will negatively impact top speed.

### Steering Servo

<figure><img src="../.gitbook/assets/image (78).png" alt=""><figcaption><p>MG996R servo motor</p></figcaption></figure>

For the best steering response, a stronger servo capable of handling the extra load from tight turns at high speed is ideal. However, any servo will work, provided you can mount it. In our example, we used a MG996R servo motor. If your servo of choice does not fit in the car's servo mount, you can either modify the mount's model or print an adapter that fits your particular servo.

### Battery

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption><p>1300mAh 2S LiPo battery with XT60 connector</p></figcaption></figure>

We recommend **two-cell LiPo batteries** with XT60 connectors, which meet the following requirements:

* **A minimum capacity of 1300mAh.** The bigger your battery, the more you can test your car on a single battery charge.
* **A nominal voltage of 7.4V** (LiPo two cell batteries have this nominal voltage). Most motors work well at this voltage, and it can be used as a backup power source for the Pixy 2 as well, should you need it (Pixy 2 Vin pin takes between 6V and 10V).
* **30C discharge rate.** Motors and servos can draw high currents from your battery, and the battery must support those discharge rates in order to not get damaged.

### Display

<figure><img src="../.gitbook/assets/image (82).png" alt="" width="375"><figcaption><p>0.91" I2c display</p></figcaption></figure>

You can add a display to your car for various debugging purposes. The provided API allows **printing characters, integers, Pixy vectors and linear camera waveforms in real time.** We strongly suggest using this display to be able to see what the camera sees in real time. **This is especially useful with the linear camera, which does not have an external app like the Pixy.**&#x20;

### Receiver

<figure><img src="../.gitbook/assets/image (83).png" alt="" width="375"><figcaption><p>FS-IA6B receiver</p></figcaption></figure>
