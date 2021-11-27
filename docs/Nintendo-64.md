***
![n64](https://cloud.githubusercontent.com/assets/10035308/12213210/ca04f1fc-b631-11e5-8ae7-d402371c9124.png)
***
_The Nintendo 64 is a 5th generation gaming console released by Nintendo in 1996_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Mupen64Plus](http://www.mupen64plus.org) | n64  | .z64 .n64 .v64 | none | /opt/retropie/configs/n64/InputAutoCfg.ini **and** /opt/retropie/configs/n64/mupen64plus.cfg|
| [lr-mupen64plus](https://github.com/libretro/mupen64plus-libretro) | n64 | .z64 .n64 .v64 .zip | none | /opt/retropie/configs/n64/retroarch.cfg |
| [lr-mupen64plus-next](https://github.com/libretro/mupen64plus-libretro-nx) | n64 | .z64 .n64 .v64 .zip | none | /opt/retropie/configs/n64/retroarch.cfg |


## Emulators: [Mupen64Plus](https://github.com/mupen64plus/mupen64plus-core), [lr-mupen64plus](https://github.com/libretro/mupen64plus-libretro), [lr-mupen64plus-next](https://github.com/libretro/mupen64plus-libretro-nx)

While the Libretro cores **lr-mupen64plus** and **lr-mupen64plus-next** have the convenience of RetroArch configurations and directly reading compressed zip files, standalone **Mupen64Plus** can be more performant. At least a Raspberry Pi 2 is required for viable Nintendo 64 performance, but performance is variable across all Pi hardware. High resolutions can impact performance greatly, so most emulators default internally to the low native N64 resolution.

**lr-mupen64plus** was abandoned some years ago, so is quite outdated. **lr-mupen64plus-next** is actively developed, but may be less performant as it has more accurate emulation.

For standalone **Mupen64Plus** you may choose between the video plugins available via the [Runcommand](Runcommand.md) menu. Different video plugins have different levels of performance and compatibility, but **GLideN64** is the only one still under active development, and generally the most compatible. Raspberry Pi 0-3 have the option of **mupen64plus-auto** which automatically chooses a suitable plugin configuration for the current game.

## ROMS
Accepted File Extensions: **.z64 .n64 .v64 .zip**

**Note:** **Mupen64Plus** standalone cannot directly load compressed zip files.

Place your Nintendo 64 ROMs in 
```
/home/pi/RetroPie/roms/n64
```

## Tweaks

### Mupen64Plus

#### Auto-configuration

```
/opt/retropie/configs/all/autoconf.cfg
```

Option | Description | Value
--- | --- | ---
`mupen64plus_audio` |  enable auto configuration of audio output path | (0/1)
`mupen64plus_hotkeys` | enable hotkey auto configuration | (0/1)
`mupen64plus_compatibility_check` | enable compatibility check which alters game-related settings | (0/1)
`8bitdo_hack` |  enable 8bitdo controller mapping hack | (0/1)

```
/opt/retropie/configs/n64/mupen64plus.cfg
```

Option | Description | Value
--- | --- | ---
`[Audio-OMX]` `OUTPUT_PORT` | Audio output path is Jack or HDMI. (will be overwritten if `mupen64plus_audio` is enabled) | (0=Audio Jack / **1=HDMI**)
`[CoreEvents]` `Joy Mapping Stop` | Joystick exit button. (will be overwritten if `mupen64plus_hotkeys` is enabled) | J**X**B**Y**/B**Z** or J**X**B**Y**
`[CoreEvents]` `Joy Mapping Load State` | Joystick load state button. (will be overwritten if `mupen64plus_hotkeys` is enabled) | J**X**B**Y**/B**Z** or J**X**B**Y**
`[CoreEvents]` `Joy Mapping Save State` | Joystick save state button. (will be overwritten if `mupen64plus_hotkeys` is enabled) | J**X**B**Y**/B**Z** or J**X**B**Y** 
`[Video-GLideN64]` `EnableFBEmulation` | Enable framebuffer emulation. Games like Mario Tennis need this option to render framebuffer effects. Some games have glitches if this option is enabled. (will be overwritten if `compatibility_check` is enabled) | (True/**False**) 
`[Video-GLideN64]` `EnableLegacyBlending` | Use fixed-function pipeline instead of shaders for blending for speed. Some games have glitches if this option is enabled. (will be overwritten if `compatibility_check` is enabled) | (True/**False**)  | (**True**/False)

#### Scaling Mode

For Raspberry Pi 0-3, a bespoke SDL hint is used to scale a low resolution window up to full screen using the Pi's GPU.

`SDL_VIDEO_RPI_SCALE_MODE=x`

Value | Description
--- | ---
0 | Window resolution is desktop resolution. This is the behaviour of SDL <= 2.0.4. (default)
1 | Requested video resolution will be scaled to desktop resolution. Aspect ratio of requested video resolution will be respected.
2 | Requested video resolution will be scaled to desktop resolution.
3 | Requested video resolution will be scaled to desktop resolution. Aspect ratio of requested video resolution will be respected. If possible output resolution will be integral multiple of video resolution.

```
/opt/retropie/configs/n64/emulators.cfg
```
You can use emulators.cfg to add custom resolution startup options. Default resolution options for Pi 0-3 are 320x240 and 640x480. Note that video plugin **GLideN64** uses a native resolution scale factor parameter instead: `--set Video-GLideN64[UseNativeResolutionFactor]\=x`

## Controls

### lr-mupen64plus
**lr-mupen64plus** utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/n64/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/16599636/7f3630fc-42c0-11e6-952f-60d97a511f38.png)

### Mupen64Plus

**Mupen64Plus** configurations are automatically generated when you configure your controller for the first time in EmulationStation. They differ from the RetroArch configs listed above.

![nintendo_n64_mupen64plus_diagram](https://cloud.githubusercontent.com/assets/10035308/16599635/7f35579a-42c0-11e6-9615-9a3670932332.png)
There are two main configuration files that can be modified:
```
/opt/retropie/configs/n64/mupen64plus.cfg
/opt/retropie/configs/n64/InputAutoCfg.ini
```

**Note:** Some arcade Joysticks or non-analogue controllers may need the following tweak to the generated mapping:

```
X Axis = "hat(0 Left, 0 Right)"
Y Axis = "hat(0 Up, 0 Down)"
```
To
```
X Axis = "hat(0 Left Right)"
Y Axis = "hat(0 Up Down)"
```

#### Hotkey combinations and special buttons

Key | Description
--- | ---
Hotkey + Start | Exit emulator.
Hotkey + Left Shoulder | Load state.
Hotkey + Right Shoulder | Save state.
Left Thumb | Enable memory expansion pak.
Right Thumb | Enable rumble expansion pak.

**Note:** Hotkey and other buttons refers to those bound during [Controller Configuration](Controller-Configuration).

## Video Tutorials

<a href="http://www.youtube.com/watch?feature=player_embedded&v=4WX7RrzUtII
" target="_blank"><img src="https://i.ytimg.com/vi_webp/4WX7RrzUtII/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> |
<a href="https://www.youtube.com/watch?v=lh0n5PWN2lI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/lh0n5PWN2lI/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> 
