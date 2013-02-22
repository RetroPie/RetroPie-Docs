From [this](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=187821#p187821) forum thread:

## When it comes to uae4all, where do you place a game's adf file? 

The roms goes into

```shell
/home/pi/RetroPie/emulators/uae4all/roms/
```

## And also, where does the kick.rom go?

You should place kick.rom (if "pi" is the user you're using) at:

```shell
/home/pi/RetroPie/emulators/uae4all/
```

## How do I start the Amiga emulator?

You start your Amiga emulation like this:

```shell
cd /home/pi/RetroPie/emulators/uae4all/
./uae4all
```


***

Here is another working log, originally posted [here](http://blog.petrockblock.com/2013/02/10/retropie-project-image-download/#comment-807493306):

> So I have had some quality time with uae4all and thought to share my loggings:

> Working log for Uae4all on RPI. Petrockblog image.

> Roms
> /home/pi/RetroPie/emulators/uae4all/roms/

> Kickrom
> /home/pi/RetroPie/emulators/uae4all/

> Starting emulator:

> Alt+F1 to exit emulationstation

> cd /home/pi/RetroPie/emulators/uae4all/
> ./uae4all

> This starts the emulator. NB kick.rom has to be called:”kick.rom”, this is case sensitive. If it is called Kick.rom you will get an “error:disk not found”.

> A box will appear. Choose :”select image disk” and find the game to load in the appearing browser window. To start the game choose Run.

> Tested configurations: 
> (Throttle, Frameskip, Screen Pos, Sound)

> Result

> Bubble Bobble
> (100, 1, 8, On)
> Too fast

> (0, 1, 8, On)
> Too fast

> (0, 1, 0, On)
> Too fast, no apparent screen change

> (0, 0, 16, On)
> Too fast, slightly bigger screen

> (0, 0, 40, On)
> Too fast, screen totally out of scale

> (0, 5, 0, On)
> Too fast. Apparent speed increase with decreasing Screen Pos.

> (100, 5, 0, On)
> Too fast.

> (0, Auto, 0, On)
> Slow

> (100, Auto, 0, On)
> Even slower

> (0, 2, 0, On)
> Too fast

> (20, 2, 0, On)
> Too fast
> No sound was heard over HDMI in any case.

> Need to find out:
> How to restart emulator from game, now only kill via ssh.
> How to fit screen. Size is too big even though the overscan settings in config.txt has been activated.
> Hot keys for speed stepping.
> Keymapping.

> Keys
> F1 – pause
> Enter – seems to skip frames, like stop motion, but still goes way to fast.

> The challenge is now how to get correct speed. I have also tried Kick-off and Kickstart II, but they failed to load.

> I hope this is useful for someone trying like me to get great games working again. But as you can see there is still a way to go before the dream of kick-off + PS3 controller + couch is realised.

> Appreciate any hints and tips

> F