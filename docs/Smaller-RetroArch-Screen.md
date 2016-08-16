### Introduction

Some people like to have their gameplay on a smaller area in the middle of the screen, rather than blown up to the full display resolution of their TV.

This is especially true of handhelds like Game Boy and Game Boy Advance where the original resolution was so low that blowing these up to 1080p results in HUGE pixels.

This tutorial covers making the display of a RetroArch libretro emulator smaller and centred on the screen.

### Determine Display Resolution

If your TV is displaying at 1080p, the resolution is **1920x1080**.

If your TV or monitor displays at another resolution, find that out and keep it in mind.

You may wish to refer to the Wikipedia [Display resolution](https://en.wikipedia.org/wiki/Display_resolution) page.

### Determine Console Resolution

Find the original resolution of the console by looking it up somewhere like Wikipedia. Here are a few popular resolutions:

* GBA: **240x160**
* Game Boy: **160x144**
* Game Gear: **160x144**
* Neo Geo Pocket: **160x152**
* Atari Lynx: **160x102**
* WonderSwan: **224x144**

Later home consoles (SNES, Master System, Mega Drive) often had multiple display resolutions and are not covered by this article.

### Multiply Console Resolution

Take the original console resolution and multiply both numbers by the same amount to get a larger gameplay resolution which is still in the same aspect ratio and fits within your actual display resolution.

For example, the GBA resolution was **240x160** so we'll multiply those up by **3** to land on **720x480**. An image of this size fits within a 1920x1080 display, is smaller than the full 1920x1080 display, and is still in the same aspect ratio so the game won't look stretched.

### Centre Image

Now we've determined our actual display resolution, and the resolution we want the game shown at, we need to centre the image on screen.

To do this, we take the **(original resolution - console resolution) / 2**.

Following our example of a **1920x1080** screen showing a **720x480** GBA image, do the following:

**(1920 - 720) / 2 = 600** is how far to offset horizontally.

**(1080 - 480) / 2 = 300** is how far to offset vertically.

### Edit Configuration File

Look at the console-specific page in the sidebar of this wiki and note where the system's configuration file.

For example, the GBA config file is `/opt/retropie/configs/gba/retroarch.cfg` so any changes made in there will apply only to GBA games, not to other systems.

Now add the following above the `#include` line in that file:

~~~
# 19 = Config, 20 = 1:1 PAR, 21 = Core Provided, 22 = Custom Viewport
aspect_ratio_index = "22"

# these two define the pixel size of the emulated screen
# keep this in the same ratio as the original console
# eg: GBA 240x160 * 3 = 720 x 480
custom_viewport_width = "720"
custom_viewport_height = "480"

# the following two decide how far from the left and top the game screen is shown
# to centre the game display use your original resolution, minus the screen size, divided by two
# this example for 1080p screen (1920x1080)
# (1920 - 720) / 2 = 600
custom_viewport_x = "600"
# (1080 - 480) / 2 = 300
custom_viewport_y = "300"
~~~

Now when the desired console is started, the game should display in a smaller area in the middle of the screen.