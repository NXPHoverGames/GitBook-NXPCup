# Linear camera

The Linear camera driver is suitable for 128x1 cameras. It automatically sends the clock and shutter signals to the camera and stores the analog values in an array.

Note: The driver does not provide a function to get the values. Instead, you should declare the buffer as an extern variable like in the example to get the values directly from the driver.

#### Initialization

```c
void LinearCameraInit(Pwm_ChannelType ClkPwmChannel, Gpt_ChannelType ShutterGptChannel, Adc_GroupType InputAdcGroup, Dio_ChannelType ShutterDioChannel);
```

Parameters:

·       ClkPwmChannel: The Pwm channel configured for the camera in the Peripherals tool.

·       ShutterPwmChannel: The Pwm channel configured for the camera in the Peripherals tool.

·       InputAdcGroup: The Adc Group configured for the camera in the Peripherals tool.
