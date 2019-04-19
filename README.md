# Freeplay-Custom-Addon-Board

![Rev 2](https://github.com/porcinus/Freeplay-Custom-Addon-Board/blob/master/preview/02.jpg)
![Rev 3](https://github.com/porcinus/Freeplay-Custom-Addon-Board/blob/master/preview/04.jpg)

The idea about this project is to combine all additional features you could need on a handheld machine but keeping modification on the motherboard as low as possible.

The PCB borders, headers position, CPU heatsink clearance and L2/R2 switches positions are the same.

This addon board embed a USB Nanohub with 2 ports, a BL-R8188FU3 WiFi module (RTL8188FTV with IPEX connector), a DS3231M RTC chip, 3 MCP3021A ADC chips (2 chips for the the Joystick and one for the battery monitoring), a 16x16x4.5 fan (the same used in the original addon board). Revision 3 now use a ADS1015 to allow use of 2 joystick at the same time.

Due to USB hub and WiFi module needing to be in the USB header side, the fan position has been switch to the other side of the CPU heatsink but because of this the hotkey switch needed to be moved as well.
A AMS1117-3.3 is used to power the WiFi module and the ADC chips reading the joystick position.

Following recommendation from Flavor (https://github.com/TheFlav), the ADC chip used to monitor battery voltage is running at 4.5v using a MAX6107 voltage reference chip.
The battery voltage also feed the VBAT pin on the RTC chip, the power consumption when the console is off is negligible.

The fan is still controlled with pin 40 using a NPN transistor.

*.cb files can be open with CamBam CNC Software (http://www.cambam.info/).


# Revision
- rev0 : initial version, ADC chip placed the wrong way, voltage divider used to power battery monitoring chip.
- rev1 : partial file, traces rework, ADC chip used to monitor battery run at 5v (could not work because I2C bus run at 3v3).
- rev2 : traces reworked, ADC chip used to monitor battery run at 4.5v via a voltage reference chip, this revision work fine in the real world.
- rev3 : X and Y ADC chips replace by a ADS1015 to allow use of 2 joystick with adress 0x48, AMS1117-3.3 regulator now use 22µF capacitor.

