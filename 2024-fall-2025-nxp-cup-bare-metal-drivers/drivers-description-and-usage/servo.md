# Servo

This driver is designed to control a servo motor via PWM (Pulse Width Modulation) signals. It allows for precise positioning of the servo arm by varying the duty cycle of the PWM signal.

#### Initialization

```c
void ServoInit(Pwm_ChannelType ServoPwmChannel, uint16 MaxDutyCycle, uint16 MinDutyCycle, uint16 MedDutyCycle);
```

This must be called before any other servo function in your program. The function sets the servo to its neutral position after initialization.

Parameters:

·       MaxDutyCycle: The maximum duty cycle, which corresponds to the servo’s maximum rotation angle.

·       MinDutyCycle: The minimum duty cycle, corresponding to the servo’s minimum rotation angle.

·       MedDutyCycle: The medium duty cycle, representing the neutral or center position of the servo.

#### Steering

```c
void Steer(int Direction);
```

This function is used for setting specific steering angles. It takes integer values between -100 and 100, with -100 being full left and 100 being full right.

Parameters:

·       Direction: Positive Direction values turn the servo right, and negative values turn it left.

#### Predefined steering angles

```c
void SteerLeft(void);
void SteerRight(void);
void SteerStraight(void);
```

·       SteerLeft: Moves the servo to its maximum rotation angle (left).

·       SteerRight: Moves the servo to its minimum rotation angle (right).

·       SteerStraight: Aligns the servo to its neutral position (center).
