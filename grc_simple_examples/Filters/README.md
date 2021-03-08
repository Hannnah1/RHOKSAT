## Intro 
The .grc file has an example which takes an input file and allows you to switch the filter being used.  
To expirament with different filters just move the arrows to the one you want to use. Anything that requires an output that you do not want to use can be connected to a `Null Sink`.

## Block descriptions
* **Sample Rate** - The sample rate is set to 48kHz because that is the sample rate of wav files. If you expirament with this variable you will be able to hear the output be distorted. If you change the input source you may need to change this to match.
* **Rational Resampler** - This is used when we need a different sample rate than what we have for blocks in the flowgraph. Decimation is the sample rate you have, and interpolation is the sample rate you want.
* **Multiply Const** - *  Multiplies by a constant value. This is not as trivial as it may seem however. One usecase is lowering the number of IQ samples on the transmit side. If you transmit at to high of a power it can interfere with the receiver. 
* **Low Pass Filter** - Blocks **HIGH** freguencies from passing. by shrinking the `cuttof_freq` paramter you can hear a smaller frequency range.
* **Band Pass Filter** - Filters out the extremely low and high frequencies. Only allows the miid-range frequencies to pass through. If it were a real circut this means the high level frequencies would be mostly filtered out by the capacitor,and the low frequencies by the inductor. Thus the middlevel frequencies would have the highest voltage going out of the circut. No idea how this works in software.
* **Notch Filter** - The exact opposite of a bandpass filter. It omits the midrange frequencies and only allows low and high through. Used a lot to make Scifi sounds.
* **FIR Filter** - Finite impulse response. Dellays the signal a certian number of blocks and then multiplies the blocks by an exponent and then adds them.


## Important Terms and definitions
* **Baseband Signal** - Signal carrying pure information. It has not been altered by any type of modulation.
* **Passband Sample** - A modulated signal. This is almost always what gets sent over the air.
* **Nyquist Sampling Rate** - Law that you need to sample at ATLEAST 2x the frequency rate.
* **Power Squelch** - Some sort of device (a software block in gnuradio) that blocks signals from being processed if they are outside of a certian range. I think this is used for making sure we can leave the system running and not process background noise when there's no signal.
*  **Doppler Correction** - We use a Cosine modulated signal source and a multiply. (Usually on a few Khz of shift is necessary)
*  **Samples per Symbol** - How many bits does it take to encode one symbol.
*  **Clock Recovery** - figures out where the spacings are between the 1's and 0's (GFSK) ???

