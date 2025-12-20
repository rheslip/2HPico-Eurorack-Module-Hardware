# 2HPico-Eurorack-Module-Hardware
2HP Eurorack module based on Raspberry Pi Pico 2

KiCad design files, BOM and gerbers for main board and panel board
Version 1.0 December 2025

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0607.JPG)

***Panel PCB Build notes***

Solder the .1u cap and the RGB LED

Solder the jacks - note that the two bottom ones have the same GND via to save real estate

Solder the button

Solder the pots. I clipped the brackets near the bend to make soldering a bit easier. Make sure they are lined up vertically and horizontally before you solder the brackets to the pads. A Panavise is handy for this step.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0590.JPG)


***Main PCB Build Notes***

I generally solder all the 0603 Rs and Cs first

Solder diodes, U3 regulator, U4 voltage reference and power connector J4. Hook it up to power and check that the 5V, -12V, +12V and -10v reference voltages are OK

Solder in all the chips, the larger caps and the trimpot RV1

The Waveshare RP2350 board cannot solder directly to the main PCB because it has components on the bottom side and must stand off a bit. You can solder .1" headers to it and solder the headers to the main PCB or solder .1" header pins in the corners and make the rest of the connections with short wires.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0595.JPG)

Power up the PCB again and check that the 5V and 3.3V rails are OK.

Solder right angle connectors J1, J2 and J3. The short pins solder to the main PCB.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0593.JPG)

Plug the long end of the right angle connectors into the panel PCB and solder.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0599.JPG)

Clip the pins on the bottom side of the main PCB so they don't interfere with adjacent modules - 2HP is only 10.16 mm panel width.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0596.JPG)

Solder one of the jumper pads on the bottom to select jack 2 on the panel as either DAC right channel out or a second CV/Gate input.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0601.JPG)

It should be ready to go. You can load up the HWtest sketch and run it to check the pots, button, inputs and DAC functions

Notes on PT8211 - I bought 10 on Aliexpress and I got a couple of defective ones. Symptom was no output from either left or right DAC, just a low amplitude glitch at the opamp outputs U6 pins 1 and 14. I suggest you buy from a couple of different vendors and cross your fingers. Alternatively Sparkfun and PJRC sell PT8211 kits for a few dollars that include 1 PT8211 presumably from a reputable source.







