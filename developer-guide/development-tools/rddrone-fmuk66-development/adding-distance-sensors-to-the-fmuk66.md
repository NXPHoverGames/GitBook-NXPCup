---
description: >-
  This pages shows how to implement the usage of distance sensors to the FMUK66
  in Hardware and with the PX4 Autopilot firmware.
---

# Adding distance sensors to the FMUK66

## Purpose of the section

This section shows the benefits of using the PX4 Autopilot firmware while using sensors which are listed [here](https://github.com/PX4/PX4-Autopilot/tree/master/src/drivers/distance_sensor). PX4 is an open-source flight controller software which provides tools for developers to create their own solutions. For more information see: [PX4](https://px4.io/)

Here the aspect of the messaging principle \(**uORB**\) is highlighted using the example of adding distance sensors. This technique can be adapted to other use cases. It is recommended to search for known topic before creating own topics. For more information about uORB see this page: [uORB Messaging](https://dev.px4.io/master/en/middleware/uorb.html)

## Hardware Integration using the Example of the VL53L0X Time-of-Flight Sensor

The VL53L0X TOF-sensor has an I2C interface for communication. The FMUK66 has only one external connector for I2C and this is used to connect the Pixy 2 camera. There are two solutions: 

1. Build an Y-adapter to connect multiple devices to this one connector, or
2. Build a SPI cable for the Pixy 2 camera and write a driver for SPI communication with it.

The recommended solution is the adapter.

Building the adapter is very easy. The following components are needed:

* PCB \(about 1-2 cm each side\) with 2.54 pitch \(minimum width: 5 pins in a row\)
* 3x Pins \(male header\), 4 pins, 0.1 inch \(2.54 mm\) spacing
* 4x female header, 4 pins, 0.1 inch \(2.54 mm\) spacing
* GHR-05V-S connector from JST
* AGHGH28K305 cable for the JST connector
* Soldering equipment

TBD: picture of the adapter

The male header must be soldered to the PCB so that it acts as a bridge. Solder the header next to each other and connect the pins from the bottom side in rows. Prepare the connectors from your devices so that every signal is on the same pin. As such, Pin 1 is always Vcc and Pin 2 GND, Pin 3 is SCL and Pin 4 is  SDA. Then connect the devices so that Vcc is connected to Vcc, GND to GND and so on. Prepare a cable with the JST connector and the AGHGH28K305 cables in the same way. Now connect the bridge with the devices and the with the FMU. The hardware setup is now done.

## Integration of the VL53L0X Time-of-Flight Sensor in Software

As considered above, PX4 has its own messaging called uORB. uORB is based on a publish-and-subscribe principle. Modules and driver can publish their values on their topic and other modules can subscribe this information. There are some distance sensors implemented in PX4 which can be used such as the VL53L0X Sensor.

For the first test, the sensor can be connected with the FMU and the FMU must be powered and connected to a computer. The FMU must be accessible via the Nuttx shell \(see [here ](https://nxp.gitbook.io/nxp-cup/developer-guide/development-tools/rddrone-fmuk66-development/commissioning-the-rddrone-fmuk66/the-example-application#user-interface)for how to use\). To connect the Sensor to the system type `vl53l0x start -X 0` in the console. The sensor is now registered as a distance sensor and the values can be read by subscribing the `distance_sensor` topic.

If you want to connect this sensor to the system by default, the command `vl53l0x start -X 0` must be added to the file `ROMFS/px4fmu_common/init.d/rc.sensors` somewhere below the section "begin Optional drivers".

The sensor data can be subscribed as shown below:

1. Include the right header:

`#include <uORB/Subscription.hpp>  
#include <uORB/uORB.h>  
#include <uORB/topics/distance_sensor.h>`

2. Create an instance of the `distance_sensor` topics:

`uORB::Subscription distance_sensor_sub{ORB_ID(distance_sensor)};   
struct distance_sensor_s distance_sensor;`

3. For reading the data run the command:

`distance_sensor_sub.copy(&distance_sensor);`

4. The possible variables and values listed for this topic are listed in the file: `msg/distance_sensor.msg`. Here the possible variables and values listed which are published on this topic. A specific variable can be read by calling `distance_sensor.[name-of-the-variable]`.

#### Example: Printing the minimum and maximum range of the sensor to the shell

`PX4_INFO("Max distance: %2.2f, Min distance: %2.2f\n", (double)distance_sensor.`**`max_distance`**`, (double)distance_sensor.`**`min_distance`**`);`

## Conclusion

Under the section `src/drivers` a selection of already available sensors can be found and are ready to use with the PX4 code. It is worth having a look there while searching for any mobile robotics related sensor. It is an easier implementation if existing modules can be used. But in case you need to use a sensor not listed there, the drivers are a good example for your own implementation and it is highly recommended to use the structure and philosophy of how to code in the PX4 environment.

