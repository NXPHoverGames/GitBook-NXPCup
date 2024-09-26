# PPM Receiver

This driver is meant to be used with a **FS-IA6B Receiver set in PPM mode**, or any other 8-channel receiver with PPM support. _This is the receiver supplied in past competitions_. The driver decodes 8 channels and makes their values available for various uses. Each of the eight channels are mapped to different switches and actuators on the RC remote. The driver automatically decodes the channels after initialization.

#### Initialization

```c
void ReceiverInit(Icu_ChannelType ReceiverIcuChannel, Gpt_ChannelType ReceiverGptChannel, uint16 ChannelMinTicks, uint16 ChannelMedTicks, uint16 ChannelMaxTicks, uint16 OutsideChannelTicks);
```

Parameters:

·       ReceiverIcuChannel: The Icu channel configured for the receiver in Peripherals tool.

·       ReceiverGptChannel: The Gpt channel configured for the receiver in Peripherals tool.

·       ChannelMinTicks, ChannelMedTicks, ChannelMaxTicks, OutsideChannelTicks: The number of ticks for shortest, median and longest PPM signal length, as well as minimum signal length for the idle signal between channels. These values should be left as is unless the driver clocks, prescalers etc are changed.

#### Getting channel values

```c
int GetReceiverChannel(uint8 Channel);
```

This function is used to get the value of a channel. The values are typically between -100 and 100, with two exceptions: when the receiver does not output any signal, it returns -200; small timing issues due to software decoding can add or subtract small amounts, going past the -100 to 100 range.

#### Getting receiver states

```c
enum ReceiverStates GetReceiverState(void);
```

This function is used to get the state machine's current state, for debugging purposes (Ex. print current state on screen).

#### Relevant structures

```c
enum ReceiverStates{
    UnSynced, /*this State indicates the program is not synced with the Receiver. Either there is
    * no signal from Receiver, or the program is unable to synchronise with it
    * (just started program/bad signal/connection lost with remote)*/
    Channel1, /*right joystick left/right movement*/
    Channel2, /*left joystick up/down movement*/
    Channel3, /*right joystick up/down movement*/
    Channel4, /*left joystick left/right movement*/
    Channel5, /*SWA (leftmost switch with 2 positions)*/
    Channel6, /*SWB (left middle switch with 3 positions)*/
    Channel7, /*SWC (right middle switch with 3 positions)*/
    Channel8, /*SWD (rightmost switch with 2 positions)*/
    BetweenChannels /*this State represents the time between two transmissions*/
};
```

```c
typedef struct{
    Icu_ChannelType IcuChannel;/*icu channel configured for the Receiver*/
    Gpt_ChannelType GptChannel;/*Gpt channel for detecting synchronisation errors*/
    uint16 ChannelMinTicks;/*minimum value in ticks a channel can have*/
    uint16 ChannelMedTicks;/*channel middle/idle value in ticks*/
    uint16 ChannelMaxTicks;/*maximum value a channel can have in ticks*/
    uint16 OutsideChannelTicks;/*minimum value that represents the area between the ppm signals*/
    Icu_ValueType Channels[8U];/*stores values received for all Channels*/
    enum ReceiverStates State;/*variable that keeps track of the State machine*/
}Receiver;
```
