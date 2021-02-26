* **Random Source** - Used to transmit a bytestream.  the `Maximum` value should be the number of bytes you want to appear in the stream + 1.
* **UChar To Float** - Needs to be used whenever we have a bytestream. We need to use unsigned to be able to view using the Histo Sink and Scope Sink blocks.
* **Band Pass Filter** - Filters out the extremely low and high frequencies. Only allows the miid-range frequencies to pass through. If it were a real circut this means the high level frequencies would be mostly filtered out by the capacitor,and the low frequencies by the inductor. Thus the middlevel frequencies would have the highest voltage going out of the circut. No idea how this works in software.

### Modulators
* **DPSK Mod** - the `Type` Parameter detemines how many bits are consumed per iteration. More on that [here](https://en.wikipedia.org/wiki/Phase-shift_keying).
`Differential Encoding`does something with xor-ingb    the bytestream. It makes it so we don't have to manually ensure that the demodulator is correctly synched with the modulator. (Cary waves have the same reference).
`Samples/Symbol` - how many complex baseband samples will be output per incoming symbol. (The interpolation factor that the resampler applys to the [internal pulse-shaping filter](https://en.wikipedia.org/wiki/Raised-cosine_filter)).
The `Excess BW` controls the Roll-off factor.
* **Constellation Sink** - Displays the resulting symbols on the complex plane.
