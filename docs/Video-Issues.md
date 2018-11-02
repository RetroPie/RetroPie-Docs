Setting in `/boot/config.txt`
```
hdmi_drive=2
```
seems to solve issues related to HDMI in some cases.


#### Can't change Resolution
If you have had to use 

```
hdmi_safe=1
```

to make your pi display on your display, you will only be able to get 640x480 resolution. To fix this you need to use these settings to allow different resolutions.

```
hdmi_force_hotplug=1
hdmi_drive=2
```
and then set 
```
hdmi_group=1
hdmi_mode=16
```
to force a resolution (those settings are for 1080p 60hz). More options can be found at: http://elinux.org/RPiconfig#Video_mode_options

An example of a forced 4:3 ratio at 1024x768

```
hdmi_drive=2
hdmi_force_hotplug=1 
hdmi_group=2 
hdmi_mode=16 
```

#### Show and set the current video mode

***Note:** This guide is only for operating systems that use `tvservice` to change the video mode, e.g. Raspbian, Xbian, and OSMC.*

`tvservice -s`will show the current video mode. Example:
```
tvservice -s
state 0x12000a [HDMI DMT (51) RGB full 4:3], 1600x1200 @ 60.00Hz, progressive
```
The option `-m` will show the CEA (HDMI) and DMT (DVI) modes that are supported by the display device:
```
tvservice -m CEA
tvservice -m DMT
```
The preferred mode that is listed as `(prefer)` can be set by the `-p` option:
```
tvservice -p
```
Any other mode has to be specified by its Group (CEA or DMT) and the mode number that was listed by the `-m` option. Example for the mode 1600x1200 @ 60.00Hz in the example above:
```
tvservice -e "DMT 51"
Powering on HDMI with explicit settings (DMT mode 51)
```

#### Reset the frame buffer after changing the video mode

After changing the video mode via `tvservice`, it may neccessary  to reset the frame buffer. This can be achieved by changing its colour depth to 8 and then back to 16:

```
fbset -depth 8 && fbset -depth 16
```

#### Switch the display off and on again

The `-o` (off) option of `tvservice` disables the video output. It can be switched on again by either the `-p` (preferred) option or the `-e` (explicit) option, see above. Example:
```
tvservice -o
Powering off HDMI
tvservice -p
Powering on HDMI with preferred settings
```
