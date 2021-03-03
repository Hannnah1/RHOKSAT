# Intro and Environment Settup
Once the cubesat is in space we will communicate with it using a LimeSDR and gnuradio.  
Most of the tools we are using are built for linux so we opted to run everything on [Ubuntu 20.04](https://releases.ubuntu.com/20.04/).
To replicate the setup any LTS version of Ubuntu should work. After intalling, be sure to run `sudo apt-get update && apt-get upgrade` before proceding.
## Gnuradio
Once you have an ubuntu system up and running, gnuradio can be installed following [these instructions](https://wiki.gnuradio.org/index.php/InstallingGR)
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
To test our setup we first created an fm transmitter and receiver. The grc block diagrams can be found [here](fm) along with a description of each of the blocks
