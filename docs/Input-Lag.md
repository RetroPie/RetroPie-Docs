Input Lag describes the delay between pressing a button on the controller, and the corresponding action being performed on screen. Typical HDTVs perform 'post-processing' on images before they are displayed, causing a delay. Wireless controllers can also add additional delay. Finally, running emulators on computer operating systems can add more delay in excess of the original hardware.

Typically, emulated games come from the CRT and wired controller era. Digital controllers connected to dedicated games consoles, pumping raw analogue images straight to the screen. The games created for them assumed this level of response, and were fast and unforgiving.

Input Lag, therefor, can be a real problem in a RetroPie environment, but fortunately there are a number of simple fixes:

## Set TV to 'GAME MODE'
Almost every HDTV or monitor will have a way of setting any given AV channel to a special mode that cuts out all non-essential post-processing, ensuring the lowest possible response time. This mode is generally called 'GAME MODE', and can be activated by switching to the AV channel used for RetroPie, and searching in the display or picture options for such an option.

## HDMI source
Certain models of older Vizio TVs (and possibly others) may exhibit input lag after switching over to the Raspberry Pi from a different HDMI source. Users have discovered that if the TV's HDMI input for the Pi is already selected/activated when the TV is powered on (as opposed to a Blu-ray player, game console, etc.), this input lag can be avoided.[source](https://retropie.org.uk/forum/topic/8552/psa-possible-source-of-controller-input-lag)

## Use wired controllers
Whilst wireless controllers are a brilliant innovation, they can add further delay. Some users report having less input lag using a bluetooth dongle rather than the Raspberry Pi 3's onboard bluetooth.

***

## Cautionary Tweaks
The internet is full of input lag configuration changes for RetroPie. However, some will have unwanted side effects, or no effect whatsoever. Listed below are a few examples.

### `video_hard_sync`
```
video_hard_sync = true
video_hard_sync_frames = 3
```
These have no effect on a Raspberry Pi, which cannot use `video_hard_sync` in any capacity.

### `dispmanx`
```
video_driver = dispmanx
```
`dispmanx` is a 'bare-metal' graphics API, with which a Retroarch video driver has been written. Whilst it can shave a frame of input lag compared to the default `gl` video driver, it also has several issues:
* No rotation support (vertical games appear on their side)
* No OSD support (no more yellow text notifications)
* No shader support

### `video_frame_delay`
```
video_frame_delay = (0-15)
```
This is a complex setting that can reduce input lag at the cost of CPU usage. Emulation on even a Raspberry Pi 3 has very little headroom, so almost any change from the default will cause stuttering in certain situations, depending on the core. That being the case, it may be more advisable to use this as a system-level, or even game-level setting.

### `video_max_swapchain_images`
```
video_max_swapchain_images = 2
```
This setting switches between using two or three buffers for rendering. Without going into details, a setting of 3 allows the emulator to run ahead and prepare the next frame before the current one has even been shown. This improves performance (i.e. makes framerate hiccups less likely), especially on slow hardware, but increases input lag by one whole frame in the general case.

In RetroPie, the default is 3. A setting lower than this will likely cause performance issues, even on a Pi 3.

### `video_threaded`
```
video_threaded = false
```
Another setting that can reduce input lag, but will reduce performance by forcing both emulation and video tasks to be executed on the same core, rather than default of 'threading' (sharing) these tasks across multiple cores. Again, this may be better suited at a system-level, or game-level setting.