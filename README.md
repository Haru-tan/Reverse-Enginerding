# <p align='center'>4x4 Modification For MiniDSP OpenDRC-DI</p>

<p>
  <img align="left" height="430" width="489" src="https://i.imgur.com/W9s2X8O.png" title="hover text"><img  src="https://i.imgur.com/jvzI6ht.png">
  </p>


I thought it might be fun to share a simple modification which I recently made to one of my MiniDSP units. This will also be applicable to anybody in possession of 
a standalone miniSHARC and DIGI-FP board. Before jumping into the work, I am going to share a little bit of background information but feel free to skip this. 
You will not miss anything critical.


<p align="center">

</p>

The MiniDSP OpenDRC-DI is marketed as a stereo (2x2) DSP intended for use as a DIY room correction solution or digital crossover. 
In reality, the unit is simply a miniSHARC (4x8) in a box, with most of the channels hidden from the user.

<img src="https://i.imgur.com/l7YQCKS.png"><img src="https://i.imgur.com/DS1ZnvO.png">

The rear panel offers several pairs of digital inputs and outputs but only one pair can be used at a time. This is because all of the panel's IO is fed to 
an SRC43821; a two channel I2S-SPDIF transceiver which doubles as a switch. Being a two (I2S) channel transceiver, it can connect only one pair of inputs and 
outputs to the miniSHARC board at a time but this strikes me as a rather lazy implementation for reasons that will soon become apparent.

<p align="center"><img src="https://i.imgur.com/0Sr1Q79.png"></p>

Looking at the pinout for the miniSHARC's J2 expansion header, we can see that it offers onboard TTL SPDIF RX and TX. Ordinarily, making use of this IO 
would require fiddly level conversion from TTL to coax levels but as you may have noticed, we already have both TOSLINK RX and TX modules on the rear panel board. 
These TOSLINK modules require TTL SPDIF, which is exactly what the miniSHARC offers.

If we hijack these modules and route their RX/TX pins directly to the corresponding pads on the miniSHARC's J2 header, this will turn the OpenDRC-DI into a 
4x4 device without the need for any additional hardware. Rather than having wasted connectors on the rear panel, both the coaxial SPDIF and TOSLINK can be used 
simultaneously and independently.

<img src="https://i.imgur.com/wvALCxI.png">

So, let's do just that! Remove the rear panel board from the chassis, flip it over and solder a wire to the RX/TX pins of the TOSLINK modules. 
The original trace connecting the RX module to the SRC43821 can be left alone but the TX module's trace needs to be cut. Otherwise, we would be shorting the 
TTL outputs and that is never a good idea.

<img src="https://i.imgur.com/wouM5PV.png">

We can then replace the rear panel in the chassis and solder each of those wires to the corresponding SPDIF RX and TX pads on the miniSHARC. 
The modification is now complete and the chassis cover can be replaced.

In order to make use of these additional channels, you will need to use the miniSHARC 4x8 plugin rather than the OpenDRC 2x2 plugin. 
Here is a simple demonstration, wherein four input channels are combined using the matrix mixer in the miniSHARC 4x8 plugin.

<img src="https://i.imgur.com/YdJGEWb.jpg">

Those feeling a little bit adventurous could take this modification further with a pair of WM8805 boards, in order to make use of the remaining four output 
channels (which I have done). The miniSHARC is a 4x8 device, after all.

