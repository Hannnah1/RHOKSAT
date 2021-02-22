* **Random Source** - Used to transmit a bytestream.  the `Maximum` value should be the number of bytes you want to appear in the stream + 1.
* **UChar To Float** - Needs to be used whenever we have a bytestream. We need to use unsigned to be able to view using the Histo Sink and Scope Sink blocks.

### Modulators
* **DPSK Mod** - the `Type` Parameter detemines how many bits are consumed per iteration. More on that [here](https://en.wikipedia.org/wiki/Phase-shift_keying).
`Differential Encoding`does something with xor-ingb    the bytestream. It makes it so we don't have to manually ensure that the demodulator is correctly synched with the modulator. (Cary waves have the same reference).
`Samples/Symbol` - how many complex baseband samples will be output per incoming symbol. (The interpolation factor that the resampler applys to the [internal pulse-shaping filter](https://en.wikipedia.org/wiki/Raised-cosine_filter)).
The `Excess BW` controls the Roll-off factor.
* **Constellation Sink** - Displays the resulting symbols on the complex plane.
