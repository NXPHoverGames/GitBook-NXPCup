# Pixy camera

The Pixy2 camera driver communicates via I2c to get all the detected vectors and their indexes.

#### Initialization

```c
void Pixy2Init(I2c_AddressType PixyI2cAddress, uint8 PixyI2cChannel);
```

Parameters:

·       PixyI2cAddress: The I2c address configured on the Pixy2 via the Pixymon app.

·       uint8 PixyI2cChannel: The I2c channel configured for the camera in the Peripherals tool.

#### Setting the RGB LED color

```c
void Pixy2SetLed(uint8 Red, uint8 Green, uint8 Blue);
```

Useful for debugging purposes

Parameters:

·       uint8 Red, Green, Blue: The desired LED color values, between 0 and 255.

#### Getting the detected vectors

```c
void Pixy2GetVectors(DetectedVectors *DetectedVectors);
```

Parameter:

·       DetectedVectors: The address of the variable where to store the vectors. The buffer must be declared by the user.

#### Relevant structures

```c
typedef struct{
    I2c_AddressType I2cAddress;
    uint8 I2cChannel;
}Pixy2;
```

```c
typedef struct {
    uint8 NumberOfVectors;
    Vector Vectors[100];
} DetectedVectors;
```

```c
typedef struct{
    uint16 x0, y0, x1, y1;
    uint8 VectorIndex;
}Vector;
```

Note: The last two structures are not defined in pixy2.h, but in main\_types.h, as they are used by other car drivers too.
