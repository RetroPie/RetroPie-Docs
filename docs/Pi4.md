#Raspberry Pi 4 and Retropie [Draft]

Raspberry Pi 4B specific questions, configuration and differences to previous models.

## Which PI 4 model ?

There are currenlty 3 Raspberry Pi 4 models available, differentiated only by the RAM option - 1Gb, 2Gb or 4Gb. Either of them will be fine for RetroPie, the memory capacity doesn't influence the emulation speed.
  
## Hardware

### Connecting a Tv/Monitor

The Pi 4B model has 2 microHDMI ports. It's recommended to use the port adjacent to the UCB-C power input (labelled HDMI0) to connect your display, since is the only one that has sound enabled (by default) and supports CEC.
 
**NOTE**: The Pi 0 _miniHDMI_ cables are not usable for the Pi 4B _microHDMI_ ports.
 
### Analog video

Composite video from the analog RCA port is not enabled by default on the Pi 4B, you need to add `enable_tvout=1` to the `config.txt` boot configuration file. This will disable the HDMI video output, so make sure you remove this option if you change the video output on your Pi 4 to one of the microHDMI ports.

**IMPORTANT**: the configuration comes with a performance penalty. Because composite video requires a very specific clock, setting that clock to the required speed on the Pi 4 means that other clocks connected to it are detrimentally affected, which slightly slows down the entire system.

More details about video configuration options - [Video Options in the official Raspberry Pi documentation](https://www.raspberrypi.org/documentation/configuration/config-txt/video.md).

### 4k video display

 The Pi 4B can use 4k video resolutions when supported by the display. By default it will select a 30hz refresh rate for a 4k resolution. To change it 60hz refresh rate, add `hdmi_enable_4kp60=1` to `config.txt` or use `raspi-config` to enable the 4k@60Hz video mode.
 
**NOTE**: If you are using both HDMI ports of the Raspberry Pi 4 for simultaneous 4k video output, you are limited to 4k@30Hz for both displays.

#### Issues using a 4k TV

 Using a 4k resolution on the Pi 4 is still too demanding when using RetroPie, so if you have a 4k display and you're seeing slowdowns/stuttering the first time you boot, there a few options available to alleviate this issue:
 
1. Use a 1080p video mode by default.  
    Either use `Raspi Config` from the RetroPie menu in EmulationStation to set the resolution, or edit the `config.txt` file on the sdcard and add the following lines at the end:

        hdmi_group=1
        hdmi_mode=16

    You'll still be able to use 4k video resolutions in RetroPie for Kodi or the Pixel desktop, but the default resolution at boot will be 1080p.
  
2. Disable 4k video modes completely.  
    Edit the boot configuration file `config.txt` file on the sdcard and add a line with: 

         hdmi_max_pixel_freq=200000000

     The Pi will now ignore any 4k video modes and display using best matching video mode available (most likely 1080p).

#### Using 4k video with Kodi/VLC

Hardware video decoding for 4k (HEVC) video needs more memory allocated to the GPU. If you have issues with 4k videos in Kodi, then edit the `config.txt` file on the sdcard and add a line with:


    gpu_mem=320M

More info in [this topic](https://www.raspberrypi.org/forums/viewtopic.php?f=66&t=251645).
 
### Power up
  
The first Pi 4b revision (1.1) has a non-compliant USB-C charging port and doesn't work with as many chargers as it should, especially E-marked USB-C cables/chargers. This has been corrected in the 1.2 revision of the board, released Feb 2020.

If you have the official power supply for your Pi 4, you shouldn't have any problems.
  

## Software

The Raspberry Pi 4 model is supported by Raspbian starting with Raspbian Buster (based on [Debian 10 'buster'](https://www.debian.org/News/2019/20190706)), while RetroPie added support the the 4.6 image version.

### Configuration changes

* ** Memory Split** 
    Previous models' GPU memory configuration ([Memory split](Memory-Split.md)) are not needed for the Pi 4B. The 3D component of the GPU is able to use the main (ARM) memory, without any additional settings. Reserving additional memory with the `gpu_mem` configuration settings in `config.txt` is only necessary for hardware video decoding (i.e. 4k movies in Kodi).

### RetroPie changes for the Pi 4B

- uses the KMS/DRM video system for display and the `vc4-fkms-v3d` overlay to enable the firmware KMS driver.
- emulators that used directly the legacy proprietary drivers have been re-compiled for KMS support or disabled on the Pi 4. Some examples 
   - `pcsx_rearmed` is disabled since it's using the old video drivers
   - `attractmode` is disabled since it's using the old video drivers
   - `advmame-1.4`, `advmame-0.39` are not properly working with the emulated DRM framebuffer, so they're disabled
   - `advmame` is compiled and configured with the SDL2 video/input drivers, so it loses the ability to create custom video timings for emulation
