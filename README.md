# SimpsonTvReloaded

Hello and welcome to the SimpsonTvReloaded guide 🙂

The original idea is from [Brandon Withrow](https://github.com/buba447) and you can find his original build guide [here](https://withrow.io/simpsons-tv-build-guide-waveshare).

While the original idea was already awesome (😎), I wanted to bring some changes and improvements:

 - Software:
	 - Gapless Playback using VLC (instead of the abandonned and deprecated OmxPlayer)
	 - Playback control (play/pause, next, previous)
         - Current episode saving, will resume the last played episode in case of a shutdown
 - Hardware:
	 - Audio filter for the audio over GPIO
	 - USB C power instead of micro USB
	 - LiPo Battery added for a wireless experience
 - 3D Model
	 - VCR with functional buttons (used for playback)
	 - Back panel access (sturdier and no more visible seam)
	 - Front screen bezel adjusted to not cover the LCD screen

The next sections are going to cover the required tools and materials, the part to prints, the assembly and the software installation in order to build your own.

## Required tools

 - [Soldering Iron](https://www.amazon.fr/TS101-%C3%A9lectrique-Professionnel-dalimentation-Temp%C3%A9rature/dp/B0BVHM2DYX) + [solder](https://amzn.to/4c3kdym)
 - [Hot Glue Gun](https://amzn.to/4c45mnh) + [glue sticks](https://amzn.to/3wFhBpY)
 - [JST Connectors](https://amzn.to/3Tnbi36)
 - [Crimping tool](https://amzn.to/3T4gGH1)
 -  Acrylic paint

## Required materials and parts

Mandatory parts:
 - [Raspberry Pi Zero with headers](https://amzn.to/3TmvL8z) x1
 - [Raspberry Pi Pico](https://amzn.to/3wCgB62) x1
 - [Waveshare 2.8" 640x480 screen](https://amzn.to/3IkPnn2) x1 
 - [PAM8302 Audio Amplifier](https://amzn.to/4306aVS) x1
 - [1.5" 4ohm 3W Audio Speaker](https://www.amazon.fr/Hsthe-Sea-Haut-Parleur-Diam%C3%A8tre-Arduino/dp/B0BP6RNYZF) x1
 - [1K Trim Potentiometer](https://amzn.to/49YFiI8) x1
 - [Push buttons](https://amzn.to/3V3r18W) x3
 - [Momentary Push Button](https://amzn.to/3V3r18W) x1
 - [Male Micro Usb Connector](https://amzn.to/3uZe8Cf) x3
 - [Female USB C Connector](https://amzn.to/48zCxvW) x1
 - [256 Gb Micro SD](https://amzn.to/49V27wh) x1
 - [M3x5mm screws ](https://amzn.to/3IlzD31) x6

Optional parts (only if you wish to use a battery):

 - [Lipo Rider Plus](https://amzn.to/3TlO3GO) x1
 - [3.7v Lipo Battery](https://amzn.to/439JHpG) x1
 - [Male USB C Connector](https://amzn.to/3V5AbBM) x1

## Encoding the videos

This process can take quite some time if you are a completionist like me, so it is a good idea to launch the encoding process  so that the videos will be ready when you are done assembly eveything.

The goal is to encode videos in a 640x480 format, but also **ROTATE** them. 

Yes, you read that right.

Rotating them is required because of the lack of support from Waveshare, when using hardware acceleration for their 2.8" DPI screen, rotating the screen is only possible with a X environnement, but that will NOT be our usecase as it will use more resources.

I strongly advise to use [Tdarr](https://home.tdarr.io/) to automatically encode the videos, you can follow their install process : https://docs.tdarr.io/docs/installation/windows-linux-macos

I will not go into details on how to use Tdarr, but here is the plugin configuration to use in order to process the videos:

Tdarr_Plugin_00td_action_handbrake_ffmpeg_custom HandBrake or FFmpeg custom arguments
`<io> -vf "transpose=1,scale=640:480" -c:v libx264 -preset medium -crf 17 -pix_fmt yuv420p -c:a copy`

Once you have set up your library, the encoding process should start.

## Printing the parts

Download the STL files [here](#) and then print the following parts:

- `01 - TVBody.stl` x1
- `02 - TV Body Backplate.stl` x1
- `03 - VCR Modded.stl` x1
- `04 - Antenna Ball.stl` x2
- `05 - PowerButton.stl` x1 
- `06 - VolumeKnob.stl` x1

I have printed them on a resin printer, but you should be able to print those on a regular FDM printer as well.

## Painting the parts (optional)

Once parts are out of the printer, I would advise to paint them, it is easier to paint them now rather than once everything is assembled.

I used an airbrush to paint my TV, but you can do as you please.

Obviously if you don't care about painting them,  you can skip this step :)


## Assembling the parts

First of  all, solder wires to the three push buttons that will be inserted into the VCR, and insert them like so:

Once this is done, route the wires trough the top of the TV like so:

And then screw the VCR into place from the inside of the TV.
