# Display

This driver is for the display that comes with the MR-CANHUBK344 board. It is a 128x32 OLED display with a SSD1306 chip with I2c. **The chip is also found in 128x64 I2c displays, and the driver is easy to port for them**. The display is strongly recommended for easier debugging.

The driver divides the pixels into 4 lines of 16 characters each using an 8x8 character fontmap. **You can print text, positive and negative integers, waveforms and vectors with this driver.** The driver keeps a buffer of all the display’s pixels.

#### &#x20;Initialization

```c
void DisplayInit(uint8 I2cChannel, uint8 FontmapRotation);
```

Parameters:

·       FontmapRotations: If this parameter is set to anything other than zero, the fontmap will be rotated. This parameter should be kept as 1 in most circumstances.

#### Printing text

```c
void DisplayText(uint16 DisplayLine, const char Text[16], uint16 TextLength, uint16 TextOffset);
```

Parameters:

·       DisplayLine: The line on which to print the text.

·       Text\[16]: The actual text to print.

·       TextLength: The length of the text to print.

·       TextOffset: How many positions from the start of the line (left) to skip before printing the text.

#### Printing integers

```c
void DisplayValue(uint16 DisplayLine, int Value, uint16 TextLength, uint16 TextOffset);
```

Parameters:

·       DisplayLine: The line on which to print the number.

·       Value: The actual number to print.

·       TextLength: How many digits to print. If this parameter is larger than the number of digits the number has, it will be completed with blank spaces. If it is smaller, the number will be cropped to fit.

·       TextOffset: How many positions from the start of the line (left) to skip before printing the number.

#### Printing waveforms

```c
void DisplayGraph(uint8 DisplayLine, uint8 Values[128], uint16 ValuesCount, uint8 LinesSpan);
```

Parameters:

·       DisplayLine: The line on which to start printing the waveform.

·       Values\[128]: The actual values to print. The values must be in the 0-100 range.

·       ValuesCount: How many values to print. This also determines how many pixels the waveform will occupy horizontally on the display.

·       LinesSpan: How many lines should the waveform occupy vertically, starting from the DisplayLine parameter and going down. The waveform will be scaled automatically to fit.

#### Printing vectors

```c
void DisplayVector(Vector VectorCoordinates);
```

#### Clearing the display

```c
void DisplayClear(void);
```

This function clears the display’s buffer. It still needs a refresh to see the changes.

#### Refreshing the display

```c
void DisplayRefresh(void);
```

This function sends to the display the current buffer.

#### Relevant structures:

```c
typedef struct{
    I2c_AddressType I2cAddress;
    uint8 I2cChannel;
    /*this is a buffer for the displayed characters, on calling DisplayRefresh() its contents are shown on screen*/
    unsigned char ScreenCharBuffer[CharacterRows][CharacterColumns];
}Display;
```
