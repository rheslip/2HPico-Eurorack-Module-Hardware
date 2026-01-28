Design files for the 2HPico DSP PCB

The DSP version uses the same front panel board as the 2HPico but replaces the PT8211 DAC with a PCM5102A audio DAC and adds a PCM1808 audio ADC. This version is intended to be used for audio processing. 

The top input jack on the front panel can be used for audio input or CV input since its connected to both the audio ADC and the RP2350 ADC on GP26. A "DC Input" jumper has been added to the back of the PCB which shorts the DC blocking input capacitor so the top jack can be used as a CV input. 
Its recommended that this jumper be left open for audio use since it adds a ~ 1.6V offset to the input which could cause very high level audio inputs to clip in the opamp input stage. Also note that the scale of this CV input is different than the second one because the opamp gain was set for optimal audio levels.

The PCM1808 is 24 bit only and the PCM5102A is n the same I2S interface so they bot have to use the same data size. I could not get 24 bit PCM working with Pico Arduino but it does work with 32 bit PCM. The additonal overhead from 24 to 32 bit is minimal.
