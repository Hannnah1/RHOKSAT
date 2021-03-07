# Intro
This repository contains the current progress on the groundstation for the RHOKSAT. 

# Hardware
We will be using a LimeSDR for both transmitting to and receiving from the cubesat.

# Software 
Most of the tools we are using are built for linux so we opted to run everything on [Ubuntu 20.04](https://releases.ubuntu.com/20.04/).
To replicate the setup really any LTS version of Ubuntu should work. After intalling, be sure to run `sudo apt-get update && apt-get upgrade` before proceding.

### Gnuradio
Signal modulation and demodulation can all be done through gnuradio, which will communicate directly with the lime via usb.
gnuradio can be installed following [these instructions](https://wiki.gnuradio.org/index.php/InstallingGR)
run the commands under the section titled "ubuntu PPA installation"  
Next we need to install gnuradio support for the LimeSDR
That is done through a plugin with installation instructions [here](https://wiki.myriadrf.org/Gr-limesdr_Plugin_for_GNURadio)
In the very near future we will also need the blocks for satelite encoding and decoding [found here](https://github.com/daniestevez/gr-satellites)  The installation instructions can be found [here](https://gr-satellites.readthedocs.io/en/latest/installation_ppa.html#installing-using-the-ubuntu-ppa)
Important things to note about gnuradio:
  * Properties in a block that are underlined can be changed at runtime.
  * The colors corospond to the type of variable expected/produced.
  * floating point samples in gnuradio should be normalized to etween [ -1, 1 ]. This can be done using the Multiply Const` block.
  * The `Throttle` block controls the rate at which samples are processed. Typically this will depend on the hardware of the sink. In the case that we don't have a hardware sink the throttle block is used to that the samples are not bounded  by cpu (way to fast)
# Testing the setup
The `Unit Tests` directory contains some basic examples of signal processing with gnuradio. the `blocks.md` file in each subdirectory contains descriptions of the blocks used as well as the parameters we configured them with.
