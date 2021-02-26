## Intro 
The .grc file has an example which takes an input file and allows you to switch the filter being used.  
To expirament with different filters just move the arrows to the one you want to use. Anything that requires an output that you do not want to use can be connected to a `Null Sink`.

## Block descriptions
* **Sample Rate** - The sample rate is set to 48kHz because that is the sample rate of wav files. If you expirament with this variable you will be able to hear the output be distorted. If you change the input source you may need to change this to match.
* **Low Pass Filter** - Blocks **HIGH** freguencies from passing. by shrinking the `cuttof_freq` paramter you can hear a smaller frequency range.
* **Band Pass Filter** - Filters out the extremely low and high frequencies. Only allows the miid-range frequencies to pass through. If it were a real circut this means the high level frequencies would be mostly filtered out by the capacitor,and the low frequencies by the inductor. Thus the middlevel frequencies would have the highest voltage going out of the circut. No idea how this works in software.
* **Notch Filter** - The exact opposite of a bandpass filter. It omits the midrange frequencies and only allows low and high through. Used a lot to make Scifi sounds.
* **FIR Filter** - Finite impulse response. Dellays the signal a certian number of blocks and then multiplies the blocks by an exponent and then adds them.
