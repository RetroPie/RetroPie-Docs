Raspberry Pi 4B specific questions, configurations and differences.

## Which PI 4 model ?

There are currently a few Raspberry Pi 4 models available, differentiated only by the RAM option - 1Gb, 2Gb, 4Gb or 8Gb. Either of them will be fine for RetroPie, the memory capacity doesn't influence the emulation speed.
  
## Hardware

### Connecting a Tv/Monitor

The Pi 4B model has 2 microHDMI ports. It's recommended to use the port adjacent to the UCB-C power input (labelled __HDMI0__) to connect your display, since is has sound enabled by default and it's the only port that supports CEC.
 
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

         hdmi_max_pixel_freq:0=200000000
         hdmi_max_pixel_freq:1=200000000

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

###Configuration changes

####Memory Split  

Previous models' GPU memory configuration ([Memory split](Memory-Split.md)) are not needed for the Pi 4B. The 3D component of the GPU is able to use the main (ARM) memory, without any additional settings. Reserving additional memory with the `gpu_mem` configuration settings in `config.txt` is only necessary for hardware video decoding (i.e. 4k movies in Kodi).
    
####Audio Configuration

By default, only the first HDMI (HDMI0) port has audio enabled, so if you plug your TV/Monitor to the 2nd port, audio will not work.
    If you'd like to use the 2nd HDMI port, then the use the **Audio** menu in the RetroPie system from EmulationStation to choose it.

####Video drivers/GPU Changes 

The Raspberry Pi 4 model features a new GPU (Videocore VI), capable of OpenGL ES 3.2 and Vulkan. Support for the new GPU is offered GPU Mesa/Linux `v3d` driver - without support from the legacy 3D Broadcom drivers. Currently, the open source driver included in Raspbian implements OpenGL ES 3.1 and OpenGL 2.1, but support for ES 3.2 and Vulkan is under development in the upstream Mesa3d project.

Key differences from the previous Raspberry Pi models:

* the new GPU driver is implemented using the standard Linux [KMS/DRM APIs](https://en.wikipedia.org/wiki/Direct_Rendering_Manager)
* the new GPU does not offer hardware OpenVG support
* display rotation works only for simple 180 ° rotations, there's no direct rotation support for 90 ° and 270 ° (see the current [Video Documentation](https://www.raspberrypi.org/documentation/configuration/config-txt/video.md))
* directly changing the screen resolution using `tvservice`/`fbset` does not affect DRM/KMS enabled application, so dynamically changing the framebuffer resolution will not work propertly

    **NOTE** this affects the existing CRT-geared configurations or emulators that rely on `vcgencmd` to generate custom `hdmi_timings` mode and load it dynamically at runtime with `tvservice`. One alternative route would be to use X11 and `xrandr` for custom mode generation and mode switching
 
* applications using the legacy GL drivers will not function anymore, with the dreaded:

        * failed to add service - already in use?

* new ports/emulators can use the OpenGL 2.1 API.

### RetroPie changes for  Raspberry Pi 4
* [Runcommand](Runcommand.md) had extensive changes to implement video resolution switching for KMS/DRM. The option for using a different RetroArch _render resolution_ is no included when KMS/DRM is included, since it relied on _the dispmanx_ video driver for scaling the resolution.

* Emulators that used directly the legacy proprietary drivers have been re-compiled for KMS support or disabled on the Pi 4. Some examples:
   - `pcsx_rearmed` - disabled since it's using the legacy GL drivers
   - `advmame-1.4` / `advmame-0.39` - disabled because are not properly working with the emulated KMS/DRM framebuffer
   - `advmame` is compiled and configured with the SDL2 video/input drivers, so it loses the ability to create custom video timings for emulation

    For a list of emulators/packages supported on the Raspberry Pi 4, you can consult the [Platform support page](https://retropie.org.uk/stats/pkgflags/), updated automatically from the current RetroPie-Setup Github repository.

* GPIO based controller drivers might not work correctly. They are currently compatible witht the Pi 4 GPIO changes (they build and install), but due to the lack of hardware available for testing, their status should be considered experimental.  
   - Reported working - `gamecondriver`
   - Reported working - `mkarcadejoystick`. See [here](https://retropie.org.uk/forum/topic/25932/) for instructions to setup a 13 buttons configuration using the `hotkeybtn` variant of the driver.

As an alternative to the drivers included in RetroPie, [GPIOnext](https://github.com/mholgatem/GPIOnext/) can be used.    
If you happen to use one of the GPIO controller drivers, please consider testing and reporting any problems in the [RetroPie forums](https://retropie.org.uk/forums)
