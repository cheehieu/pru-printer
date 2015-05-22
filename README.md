---
layout: project
title: pru-printer
subtitle: A thermal printer reference design featuring the PRU-ICSS on the BeagleBone Black.
---

<img src="images/printer_protoype.jpg">

## Overview

A thermal printer reference design featuring the PRU-ICSS on the BeagleBone Black.

Andreas gitorious link [https://gitorious.design.ti.com/pruprinter]


Adafruit

## Hardware
PRU links

### Print Head
Fujitsu line of print heads
PRU signals selected to leave room for a display, MMC signals


### Power
The FTP print head draws a lot of current. In testing, it was possible to run the printer and supply from the 5VDC, 3A wall wart, but it may have been drawing more than 3A to power the BBB and thermal printer EVM.
Used WEBENCH to create a power solution for connecting a 12V, 5A wall wart (used for X15). The power solution utilizes a TPS54332 for 12V to 7.2V (3A) conversion to supply VH to the print head. A TPS563209 is used for 12V to 5V (3A) conversion to supply the BeagleBone Black and subsequently the Vdd print head logic supply. These components were chosen for there low BOM cost/count, small footprint, and high efficiency.

### Motor Driver


### Print Sensors
Comparators have open-collector output and can be wired-AND together. When one of the faults go low, the FAULTn pin goes low, signalling an error

### Misc.
Buffers

A standard cape EEPROM is included to store cape and pinmux information. This circuit is nearly identical to the one in the BeagleBone Black SRM. The difference being a fixed I2C address at 0x54, removing the need for a DIP switch.

A FTDI 

## Software
No software available
Port work done by Andreas
Utilize new Linux PRU-ICSS interface


## Next Steps
Finish prototype
Board bringup
Software development
