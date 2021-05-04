Input Lag describes the delay between pressing a button on the controller, and the corresponding action being performed on screen. Typical HDTVs perform 'post-processing' on images before they are displayed, causing a delay. Wireless controllers can also add additional delay. Finally, running emulators on computer operating systems can add more delay in excess of the original hardware.

Typically, emulated games come from the CRT and wired controller era. Digital controllers connected to dedicated games consoles, pumping raw analogue images straight to the screen. The games created for them assumed this level of response, and were fast and unforgiving.

Input Lag, therefore, can be a real problem in a RetroPie environment, but fortunately there are a number of simple fixes:

## Set TV to 'GAME MODE'
Almost every HDTV or monitor will have a way of setting any given AV channel to a special mode that cuts out all non-essential post-processing, ensuring the lowest possible response time. This mode is generally called 'GAME MODE', and can be activated in two ways:

### Via TV
Switch to the AV channel used for RetroPie, and search in the display or picture options for such an option.

### Via /boot/config.txt
Add the following line to `/boot/config.txt` to cause newer TVs to automatically attempt to request 'GAME MODE':
```
edid_content_type=4
```

**NOTE**: Some TVs are known to look worse via 'GAME MODE'; typically those that have atypical native panel resolusions like 1366x768, where it may force them to run at 1080p/720p, causing ugly scaling.

## Use HDTV’s native display resolution
If RetroPie outputs a resolution lower or higher than the maximum that your TV supports, your TV will always up or downscale the image to that maximum. Such operations are often VERY slow. 

By default RetroPie will output to your TV's native resolution, but this can be overridden via [Runcommand](Runcommand) - options 4 and 5 - "Video Mode". Be sure you haven’t done this by checking both of these options are set to blank for your emulators and games, which is the default.

**NOTE**: The above only applies to modern digital TVs. CRTs do not process and display video signals in the same way.

## Run the NTSC version of games.
NTSC (eg USA/Japanese) versions of games will run at 60Hz, but PAL (eg European) versions will run at 50Hz. The latter will feel noticeably slower and less responsive. 

## HDMI source
Certain models of older Vizio TVs (and possibly others) may exhibit input lag after switching over to the Raspberry Pi from a different HDMI source. Users have discovered that if the TV's HDMI input for the Pi is already selected/activated when the TV is powered on (as opposed to a Blu-ray player, game console, etc.), this input lag can be avoided.[source](https://retropie.org.uk/forum/topic/8552/psa-possible-source-of-controller-input-lag)

## Use wired controllers
Wireless controllers can add further delay. Some users report having less input lag using a bluetooth dongle rather than the Raspberry Pi 3's on-board Bluetooth.

***

## Unsupported Tweaks
The internet is full of input lag configuration changes for RetroPie. However, all those noted below will have additional performance penalties, or no effect whatsoever. All these settings are unsupported by Retropie. If you should choose to make use of them, always keep in mind that you have done so if performance issues arise and be prepare to try removing them as a potential cause.

### Video Hard Sync
```
video_hard_sync = true
video_hard_sync_frames = 3
```
These have no effect on a Raspberry Pi, which cannot use `video_hard_sync` in any capacity.

### Dispmanx display driver
```
video_driver = dispmanx
```
`dispmanx` is a 'bare-metal' graphics API for the Raspberry Pi 0-3, with which a Retroarch video driver has been written. Whilst it can shave a frame of input lag compared to the default `gl` video driver, it also has several issues:
* No rotation support (vertical games appear on their side)
* No OSD support (no more yellow text notifications)
* No shader support
* Not available on non-Raspberry Pi hardrware, or when using fkms/kms (mandatory on Pi 4)

### Frame Delay
```
video_frame_delay = (0-15)
```
This is a complex setting that can reduce input lag at the cost of CPU usage. Emulation on even a Raspberry Pi 3 has very little headroom, so almost any change from the default will cause stuttering in certain situations.

### Max Swapchain Images
```
video_max_swapchain_images = 2
```
This setting switches between using two or three buffers for rendering. Without going into detail, The default setting of 3 allows the emulator to run ahead and prepare the next frame before the current one has even been shown. This improves performance (i.e. makes framerate hiccups less likely), especially on slow hardware, but generally increases input lag by one frame. A setting of 2 allows less preparation, which will likely cause performance issues, even on a Pi 3, but potentially saving a frame of input lag.

### Threaded Video
```
video_threaded = false
```
Another setting that can reduce input lag, but will reduce performance by forcing both emulation and video tasks to be executed on the same core, rather than default of 'threading' (sharing) these tasks across multiple cores.

### Run Ahead

This Retroarch feature calculates the frames as fast as possible in the background to "rollback" the action as close as possible to the input command requested. It is a heavy task and will cause performance issues unless significant headroom is available. It can be set as a number of frames to advance the action, but settings above 1 risk going beyond the game's internal lag, causing animation glitches. Documentation on calculating the maximum Run Ahead for a given game is available [here](https://docs.libretro.com/guides/runahead/). A generally safe value to set (when the required CPU headroom is available) is 1 frames:
```
run_ahead_enabled = "true"
run_ahead_frames = "1"
```
It may be required to add the following workaround for some cores, to avoid certain save state limitations:
```
run_ahead_secondary_instance = "true"
```

## Application of Unsupported Tweaks

Whilst unsupported, careful application of some of these tweaks can be useful for certain games and systems where additional headroom is available. Therefore they should be applied at a [system level, or even a game-specific level](RetroArch-Configuration#config-hierarchy) rather than globally. The following sections detail what tweaks can be viable for certain hardware:

### Raspberry Pi 3

On Pi 3 there is very little headroom to allow these tweaks without a hit on performance in many of the available RetroArch cores. NES is a system that leaves just enough overhead on a Raspberry Pi 3 to allow the above tweaks to be implemented whilst reportedly maintaining full speed. Using it as an example, below are the four applicable tweaks that can be made to reduce input lag as much as possible on a Raspberry Pi 3, while maintaining a full 60fps in the available NES cores. The one setting that allows some flexibility is [Frame Delay](#frame-delay), but a setting above 4 is likely to reduce performance in the NES cores.

```
video_driver = "dispmanx"
video_threaded = "false"
video_frame_delay = 4
video_max_swapchain_images = 2
```

For those who wish to make use of shaders, overlays and the OSD, simply remove `video_driver = "dispmanx"`. When used with a less demanding core, `video_frame_delay`can likely be increased to some degree, with the maximum limit being 15.

Although the SNES cores should only ever have these settings applied at a game level, below is a graph depicting the effect they can potentially have, using 'Super Mario World' as an example.

![SNES Input Lag Graph](https://user-images.githubusercontent.com/18494695/38519182-f5616840-3c0c-11e8-89fb-dae734d01e81.gif)

### Raspberry Pi 4

The Raspberry Pi 4 has a significant bump in CPU horsepower, leaving some headroom for more aggressive input lag tweaks across many of the 2D cores in RetroPie. It can also be worth experimenting with [Run Ahead](#run-ahead), which is viable in most of the 2D cores.

### PC / x86 / x64

Entirely dependent on the hardware used, but there may significant headroom allowing for many of these tweaks to be set.
