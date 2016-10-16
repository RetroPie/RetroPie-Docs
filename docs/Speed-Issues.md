Systems from fastest to slowest:

* Raspberry Pi 3
* Raspberry Pi 2
* Raspberry Pi Zero
* Raspberry Pi 1

How much faster depends on the specific game and emulator you are interested in.

Most SNES, Mega Drive, GameBoy Advance, and simpler emulators should run at full speed of close on a Pi 2.

## Specific System Observations

### Arcade (MAME/FBA)

Speed depends greatly on the game and the emulator version.

Certain games are just known for being really slow, like Mortal Kombat or NBA Jam.

Certain versions of the emulators run some ROMs very fast, other versions run the same game very slowly. Earlier/later isn't always better, try different emulator versions to see which performs best for the ROM in question.

Some games will never achieve playable speeds.

### SNES

Some games, especially SuperFX and SA-1 games, will be slow on a stock speed Pi 1, but are generally playable on a Pi 3.

Some graphic effects in some games can cause lag when displaying specific screens, but the game will be playable overall.

### PlayStation, N64, Dreamcast, PSP

Due to limited processing power and/or lack of emulator efficiency, some games will never achieve playable speeds.

## Configuration Improvements

### RetroArch emulators (lr- cores)

Edit `/opt/retropie/configs/all/retroarch.cfg` and set:

```
# Use threaded video driver
video_threaded = true

# Smoothens picture with bilinear filtering
video_smooth = false

# Audio driver backend.
audio_driver = alsathread

# Enable rewinding
rewind_enable = false

# Potentially improve input lag
video_frame_delay = 5
```

The Video Hard Sync settings don't actually have any effect, as this is not available on the Pi, there is no benefit from having them set or unset:

~~~
video_hard_sync = true
video_hard_sync_frames = 3
~~~

### Resolution

Try to decrease the Render Resolution or Framebuffer Resolution in the runcommand menu, displayed just before a game starts.

Decreasing the screen size the emulator has to calculate can lead to an overall speed increase.

### TV

Ensure you're using your TV's native resolution to prevent any overhead due to upscaling. Most modern HD TVs can display at 1080p (1920x1080) and 720p (1280x720) without issue.

Enable **Game Mode** in the TV settings for the input used for the Pi. This disables some image processing (smoothing, etc) which makes movies look better, but which introduces latency when playing games.

## Overclocking

### With RetroPie Setup Script

In the menu **Setup** you can find the options for changing the ARM and SDRAM frequencies.

Changes require a reboot to take effect.

### With raspi-config

You can overclock **without voiding the warranty** with the official `raspi-config` script.

It can be started with:

```
sudo raspi-config
```
### Considerations

Heavily overclocked systems (and even regular Pi) would probably have their lifespan increased by using a heatsink.

Kits are available cheap on eBay and Amazon, the bigger the heatsink the better.

Cases with fans are also available, with the fan usually powered by the 5V GPIO pins.

## References

* [Overclocking thread on the official Raspberry Pi forum](http://www.raspberrypi.org/phpBB3/viewtopic.php?f=29&t=6201)
* [Showcase of older emulator versions on Raspberry Pi 1](http://www.youtube.com/watch?v=rm3IuXeIfaw)
* [ToadKing](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=137827#p137827)
* [ChadP](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=156971#p156971)
* [Comparison of cooling methods](https://www.youtube.com/watch?v=1AYGnw6MwFM)