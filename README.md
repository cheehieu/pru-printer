---
layout: project
title: pru-printer
subtitle: A thermal printer reference design featuring the PRU-ICSS on the BeagleBone Black.
---

<img src="images/printer_protoype.jpg">

## Overview
This project is a thermal printer reference design featuring the PRU-ICSS on the AM335x. It was inspired by a similar project by [Andreas Dannenberg](https://gitorious.design.ti.com/pruprinter). Here is a video of his prototype: [https://youtu.be/tVr5VrtNZiQ].



## Hardware

The PRU signals are connected as follows:

| BBB Pin |  PRU Signal |       Cape Signal       |
|:-------:|:-----------:|:-----------------------:|
| P8.30   | pru1_r30_11 | Vdd supply enable       |
| P8.21   | pru1_r30_12 | VH supply enable        |
| P8.20   | pru1_r30_13 | Buffer output enable    |
| P8.15   | pru0_r31_15 | Motor driver fault HEAD |
| P9.26   | pru1_r31_16 | Motor driver fault CUT  |
| P8.46   | pru1_r30_1  | MTAn_head               |
| P8.45   | pru1_r30_0  | MTA_head                |
| P8.43   | pru1_r30_2  | MTBn_head               |
| P8.44   | pru1_r30_3  | MTB_head                |
| P8.41   | pru1_r30_4  | MTA_cut                 |
| P8.42   | pru1_r30_5  | MTAn_cut                |
| P8.39   | pru1_r30_6  | MTB_cut                 |
| P8.40   | pru1_r30_7  | MTBn_cut                |
| P9.31   | pru0_r30_0  | STB1                    |
| P9.29   | pru0_r30_1  | STB2                    |
| P9.30   | pru0_r30_2  | STB3                    |
| P9.28   | pru0_r30_3  | STB4                    |
| P9.42   | pru0_r30_4  | STB5                    |
| P9.27   | pru0_r30_5  | STB6                    |
| P8.12   | pru0_r30_14 | CLK                     |
| P9.41   | pru0_r30_6  | DI                      |
| P9.25   | pru0_r30_7  | LATn                    |
| P9.24   | pru0_r31_16 | DO                      |

### Print Head
Fujitsu line of print heads
PRU signals selected to leave room for a display, MMC signals


### Power
The FTP print head draws a lot of current. In testing, it was possible to run the printer and supply from the 5VDC, 3A wall wart, but it may have been drawing more than 3A to power the BBB and thermal printer EVM.
Used WEBENCH to create a power solution for connecting a 12V, 5A wall wart (used for X15). The power solution utilizes a TPS54332 for 12V to 7.2V (3A) conversion to supply VH to the print head. A TPS563209 is used for 12V to 5V (3A) conversion to supply the BeagleBone Black and subsequently the Vdd print head logic supply. These components were chosen for there low BOM cost/count, small footprint, and high efficiency.

### Motor Driver
DRV8833C

### Print Sensors
Comparators have open-collector output and can be wired-AND together. When one of the faults go low, the FAULTn pin goes low, signalling an error
Platen open
Thermistor
Paper feed


### Misc.
Buffers
SN74LVC244A

A standard cape EEPROM is included to store cape and pinmux information. This circuit is nearly identical to the one in the BeagleBone Black SRM. The difference being a fixed I2C address at 0x54, removing the need for a DIP switch.

FTDI 

## Software
No software available
Port work done by Andreas
Utilize new Linux PRU-ICSS interface

Display
Newhaven

## Next Steps
Finish prototype
Board bringup
Software development

For more application ideas (like a cloud-connected printer), see similar hobbyist projects at [Adafruit](https://www.adafruit.com/products/1289).
