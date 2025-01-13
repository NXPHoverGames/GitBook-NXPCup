# H Bridge

This driver controls the direction and speed of two motors using a L298N H-Bridge circuit with PWM signals. It also manages braking functionality.

#### Initialization

```c
void HbridgeInit(Pwm_ChannelType Motor1_Speed, Pwm_ChannelType Motor2_Speed, Dio_ChannelType Motor1_Forward, Dio_ChannelType Motor1_Backward, Dio_ChannelType Motor2_Forward, Dio_ChannelType Motor2_Backward);
```

This must be called before any other H Bridge function in your program. After initialization, the H Bridge is set to idle speed, ready to receive speed commands.

Parameters:

·       Motor1\_Speed & Motor2\_Speed: PWM channels for controlling the speed of Motor 1 and Motor 2.

·       Motor1\_Forward & Motor1\_Backward: Digital I/O channels for setting the direction of Motor 1.

·       Motor2\_Forward & Motor2\_Backward: Digital I/O channels for setting the direction of Motor 2.

#### Setting speed

```c
void HbridgeSetSpeed(int Speed);
```

This function is used for setting specific speeds. It takes integer values between -100 and 100, with -100 being full speed backward and 100 being full speed forward.

Parameters:

·       Speed: An integer value between -100 and 100, where positive values indicate forward motion and negative values indicate reverse motion.

#### Braking

```c
void HbridgeSetBrake(uint8 Brake);
```

This function allows you to override the set speed and brake the car. **After braking, any calls to set the speed will not work. You must set the brake to 0 again to resume control of the motors.**

Parameters:

·       Brake: The car will brake if set to anything other than 0 (Ex. 1). Setting it to 0 disengages the brake and allows the car to speed up.

Parameters:

·       Brake: The car will brake if set to anything other than 0 (Ex. 1). Setting it to 0 disengages the brake and allows the car to speed up.

#### Relevant structures:

```c
typedef struct{
    Pwm_ChannelType Motor1_Speed;
    Pwm_ChannelType Motor2_Speed;
    Dio_ChannelType Motor1_Forward;
    Dio_ChannelType Motor1_Backward;
    Dio_ChannelType Motor2_Forward;
    Dio_ChannelType Motor2_Backward;
    uint8 Brake; /*value is zero or non zero: val == 0 means brake, val != 0 means no brake*/
    int Speed;    /*values between -100 and 100: val >= 0 means Forward, val < 0 means Reverse*/
}Hbridge;
```
