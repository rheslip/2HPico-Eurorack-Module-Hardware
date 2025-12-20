# 2HPico-Eurorack-Module-Hardware
2HP Eurorack module based on Raspberry Pi RP2350 Pico 2

KiCad design files, BOM, Gerbers for main board and panel board and 3D printable panel.
Version 1.0 December 2025

See the main repository for 2HPico Pico Arduino sketches to run on it.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0607.JPG)

***General notes on the design***

Waveshare (and others) make RP2040 and RP2350 boards with this small form factor and pinout. The RP2350 has much better performance but for simple things like sequencers, ADSR, LFO etc the RP2040 should work OK. Core 0 runs the main processing loop for the UI and control,
core 1 runs the DSP and sends samples to the I2S driver. The code has an option for monitoring the performance of core 1 with a scope. If enabled you will see a pulse on GPIO 8 that indicates how much time core 1 is spending processing samples. If its high more than 100% of the time you will get audio dropouts - time to overclock or optimize your code some more!

The PT8211 16 bit stereo R2R DAC is very inexpensive and has proven so far to be quite accurate and consistent from one chip to another (provided they aren't defective - see caveats below). It has no internal antialiasing filters but it works down to DC so can be used as a CV out as well. U6 is a DC coupled antialiasing filter and it also amplifies the DAC output to +-5V eurorack levels.

***Panel PCB Build notes***

Solder the .1u cap and the RGB LED. Note pin 1 location is NOT the lead with the 45 cut on it - check the picture in the BOM. Hopefully you bought the right pinout! Note these are 5V parts but I haven't had any issues running them at 3.3v - and they are still way too bright!

Solder the jacks - note that the two bottom ones have the same GND via to save real estate

Solder the button. Glue the button cap on with a dab of superglue.

Solder the pots. You can clip the brackets near the bend to make soldering a bit easier but its not required. Make sure they are lined up vertically and horizontally before you solder the brackets to the pads. A Panavise is handy for this step.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0590.JPG)


***Main PCB Build Notes***

Solder all the 0603 Rs and Cs first

Solder diodes, R1, U3 regulator, U4 voltage reference and power connector J4. Hook it up to power and check that the 5V, -12V, +12V and -10v reference voltages are OK

Solder in all the chips, the larger caps and the trimpot RV1

The Waveshare RP2350 board cannot solder directly to the main PCB because it has components on the bottom side and must stand off a bit. You can solder .1" headers to it and solder the headers to the main PCB or solder .1" header pins in the corners and make the rest of the connections with short wires.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0595.JPG)

Power up the PCB again and check that the 5V and 3.3V rails are OK.

Solder right angle connectors J1, J2 and J3. The shorter pins solder to the main PCB as shown.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0593.JPG)

Plug the long end of the right angle connectors into the panel PCB and solder.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0599.JPG)

Clip the pins on the bottom side of the main PCB so they don't interfere with adjacent modules - a 2HP module is supposed to be only 10.16mm wide.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0596.JPG)

Solder one of the jumper pads on the bottom to select jack 2 on the panel as either DAC right channel out or a second CV/Gate input. This depends on what the module is supposed to do.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0601.JPG)

It should be ready to go. You can load up the HWtest sketch and run it to check the pots, button, inputs and DAC functions


***Trimming the DAC output***

Load up the ADSR app or mod the HWtest sketch so the I2S code is sending the value 0 to the DACs. Measure the level at the output jacks or at U6 pins 1 and 14 and trim to get as close to 0V as possible. There will probably be a few mV difference between the channels. 
Its set up for +-5V output corresponding to -32767 and 32767 DAC values respectively (output amp inverts the DAC signals). If you want higher output levels you can mod the output stage gain but keep in mind the offset and the lowpass filters also have to be recalculated.


***Notes on the PT8211 DAC chips*** 

I bought 10 on Aliexpress and I got a couple of defective ones. Symptom was no output from either left or right DAC, just a low amplitude glitch at the opamp outputs U6 pins 1 and 14. I suggest you buy from a couple of different vendors and cross your fingers. Alternatively Sparkfun and PJRC sell PT8211 kits for a few dollars that include a PT8211 presumably from a reputable source.

***Notes on the Panel***

STL file is included for a 3D printable panel which includes a collimator that sits over the RGB LED. I glued a short piece of transparent filament inside the collimator as a light pipe - for some reason commercial acrylic light pipes are stupidly expensive. The RGB LED is very bright even on 3.3v so I cut the level back in the code. I will probably design a silkscreened FR4 panel for it at some point.

![](https://github.com/rheslip/2HPico-Eurorack-Module-Hardware/blob/main/Images/IMG_0608.JPG)



