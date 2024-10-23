# ESC

This driver controls the speed and direction of a motor via an Electronic Speed Controller (ESC) using PWM (Pulse Width Modulation) signals. It includes a state machine to handle the motor's operation states, such as Forward, Reverse, Braking, and Neutral.

Note: If your ESC supports braking, the driver can be configured to use it. In **esc.h,** the define **ESC\_HAS\_BRAKE** can be set to either **STD\_ON** or **STD\_OFF**. <mark style="color:red;">**If your ESC supports braking, change this parameter to STD\_ON. If it doesn't, leave it to STD\_OFF. If you are not sure, leave it to STD\_OFF. Incorrect usage can make the car go full speed backward instead of braking!**</mark>

#### Initialization

```c
void EscInit(Pwm_ChannelType EscPwmChannel, uint16 MinDutyCycle, uint16 MedDutyCycle, uint16 MaxDutyCycle);
```

This must be called before any other ESC function in your program. After initialization, the ESC is set to idle speed, ready to receive speed commands.

Parameters:

·       EscPwmChannel: The PWM channel assigned to the ESC

·       MinDutyCycle: The minimum duty cycle, corresponding to the maximum reverse speed

·       MedDutyCycle: The medium duty cycle, corresponding to the neutral or idle state of the motor

·       MaxDutyCycle: The maximum duty cycle, corresponding to the highest speed or a forward command

#### Setting speed

```c
void EscSetSpeed(int Speed);
```

This function is used for setting specific speeds. It takes integer values between -100 and 100, with -100 being full speed backward and 100 being full speed forward.

Parameters:

·       Speed: An integer value between -100 and 100, where positive values indicate forward motion and negative values indicate reverse motion.

#### Braking

```c
void EscSetBrake(uint8 Brake);
```

This function allows you to override the set speed and brake the car. If your ESC supports braking, this function will make the car actively brake. If your ESC doesn't support braking, this function will keep the speed command on 0 instead. **After braking, any calls to set the speed will not work. You must set the brake to 0 again to resume control of the motors.**

Parameters:

·       Brake: The car will brake if set to anything other than 0 (Ex. 1). Setting it to 0 disengages the brake and allows the car to speed up.

#### Getting speed

```c
int GetSpeed(void);
```

This function is used to get the last speed value set.

#### Getting brake

```c
uint8 GetBrake(void);
```

This function is used to get the last brake value set.

#### Getting current state

```c
enum EscStates GetEscState(void);
```

This function is used to get the state machine's current state, for debugging purposes (Ex. print current state on screen).

#### Relevant structures

```c
typedef struct{
    Pwm_ChannelType Channel;
    uint16 MinDutyCycle;
    uint16 MaxDutyCycle;
    uint16 MedDutyCycle;

}Esc;
```

```c
enum EscStates{
    Forward,
    Braking,
    Neutral,
    Reverse
};
```
