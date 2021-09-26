# Receivers based on Si4735 working with OLED/I2C

This folder shows some examples using the radio based on Si4735 working with OLED/I2C.


## Si47XX 01 - Arduino Library example with I2C OLED

This sketch uses the Rotary Encoder Class implementation from Ben Buxton. The source code is included together with this sketch. This sketch also uses the SSD1306Ascii Arduino Library by Bill Greiman. You can install SSD1306Ascii via Manage Libraries on your Arduino IDE. The photo below show this example on a protoboard. 

__This sketch has been successfully tested on Pro Mini 3.3V.__ 

Click [here](https://github.com/pu2clr/SI4735/blob/master/examples/SI4735_04_OLED_I2C/SI4735_04_OLED_I2C.ino) to see this example.

![Silicon Labs Schematic](../extras/images/prot_oled_01.png)


#### __ABOUT DIGITAL pin 13 and INPUT PULL-UP on Arduino Pro Mini, UNO or similar:__
This pin has a LED and a resistor connected on the board. When this pin is set to HIGH the LED comes on. If you use the internal pull-up resistor of the pin 13, you might experiment problem due to the drop voltage caused by the LED circuit. If this occurs in your project, change the circuit to use external pull-up on pin 13. 


__Click [here](https://youtu.be/7Sg4z8tDSA8) to see a video about this example__.


<BR>

## Schematic for I2C display device, buttons and encoder (used on examples "Si47XX 01" and "Si47XX 02")

The schematic below is a sugestion to connect a I2C Display (OLED or LCD 20x4 or another device), buntons and encoder as well. 

![Schematic for I2C display device](https://github.com/pu2clr/SI4735/blob/master/extras/images/basic_schematic_with_buttons_i2c.png)

__Pay attention to the your I2C device voltage. The system can become unstable if you are using a wrong voltage__.


### The picture below shows the SI4735-D60 pinout

![Si4735-D60 pinout](https://github.com/pu2clr/SI4735/blob/master/extras/images/Si4735-D60-pinout.png)



## Si47XX 02 - SI4735_02_ALL_IN_ONE_OLED - All in One Radio with SSB firmware update support

  This sketch uses the Rotary Encoder Class implementation from Ben Buxton. The source code is included together with this sketch. 

  __This sketch has been successfully tested on Pro Mini 3.3V.__ 

  This sketch will download a SSB patch to your SI4735 device (patch_init.h). It will take about 9KB from Arduino Flash Memory.   
    
  In this context, a patch is a piece of software used to change the behavior of the SI4735 device.
  There is little information available about patching the SI4735. The following information is the understanding of the author of 
  this project and it is not necessarily correct. A patch is executed internally (run by internal MCU) of the device. 
  Usually, patches are used to fixes bugs or add improvements and new features of the firmware installed in the internal ROM of the device. 
  Patches to the SI4735 are distributed in binary form and have to be transferred to the internal RAM of the device by 
  the host MCU (in this case Arduino). Since the RAM is volatile memory, the patch stored into the device gets lost when you turn off the system.
  Consequently, the content of the patch has to be transferred again to the device each time after turn on the system or reset the device.

  ATTENTION: The author of this project does not guarantee that procedures shown here will work in your development environment. 
  Given this, it is at your own risk to continue with the procedures suggested here. 
  This library works with the I2C communication protocol and it is designed to apply a SSB extension PATCH to CI SI4735-D60. 
  Once again, the author disclaims any liability for any damage this procedure may cause to your SI4735 or other devices that you are using.  

  Features of this sketch: 

  1) Internal Arduino pull-up (no external resistors on schematic for buttons and encoder);
  2) Only SSB (LSB and USB);
  3) Audio bandwidth filter 0.5, 1, 1.2, 2.2, 3 and 4Khz;
  4) Eight ham radio bands pre configured;
  5) BFO Control; and
  6) Frequency step switch (1, 5 and 10KHz);

  Main Parts: 
  Encoder with push button; 
  Seven bush buttons;
  OLED Display with I2C protocol;
  Arduino Pro mini 3.3V;  


Pay attention on the push buttons added on this example. The table below shows the commands used by this sketch.

| Defined constant | Arduino Pin | Description |
| ---------------- | ----------- | ----------- | 
| BANDWIDTH_BUTTON | 5           | Used to select the banddwith. Values: 1.2, 2.2, 3.0, 4.0, 0.5, 1.0 KHz |
| VOL_UP           | 6           | Volume Up |
| VOL_DOWN 7       | 7           | Volume Down |
| BAND_BUTTON_UP   | 8           | Next band |
| BAND_BUTTON_DOWN | 9           | Previous band | 
| AGC_SWITCH       | 11          | Switch AGC ON/OF | 
| STEP_SWITCH      | 10          | Used to select the increment or decrement frequency step (1, 5 or 10 KHz) |
| BFO_SWITCH       | 13          | Used to select the enconder control (BFO or VFO) |


__Click [here](https://youtu.be/W2Ssjb9P_f4) to see a video about this example__.

<BR>

