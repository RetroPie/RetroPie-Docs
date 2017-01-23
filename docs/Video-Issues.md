From [here](https://github.com/petrockblog/RetroPie-Setup/issues/130#issuecomment-14105633):

Setting
```
disable_overscan=1
```
in `/boot/config.txt` might solve video problems for certain setups (removes black bars around the edges). If you have installed from NOOBS, there might be 4 other lines relating to overscan directions in the config.txt, such as `overscan_left`, `overscan_top`, etc. You should deactivate these lines by placing a `#` as the first character on these lines. Note that for NOOBS installations, there might be duplicates of these lines at the bottom of the file.

Also, setting
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