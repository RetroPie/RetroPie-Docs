***
![ibmpc](https://cloud.githubusercontent.com/assets/10035308/12213490/0f8cb422-b636-11e5-99a7-2a33761874f3.png)
***
_The good old days of DOS._
***
| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [DOSBox](http://www.dosbox.com/) | pc  | .com .sh .bat .exe .conf | none | /opt/retropie/configs/pc/dosbox-SVN.conf |

## Emulator: [DOSBox](http://www.dosbox.com/), [Rpix86](http://rpix86.patrickaalto.com/)

## ROMS
Accepted File Extensions: **.com .sh .bat .exe .conf**

Place your ROMs in 
```
/home/pi/RetroPie/roms/pc
```
You can also place your games within folders in the pc folder if it helps keep you organised.

## Controls

Keyboard

**Quick Keys:**

ctrl+F9: exit emulator

For more information see http://www.dosbox.com/wiki/Main_Page

## Tutorials

[How to add games to RetroPie and launch them directly from EmulationStation.](http://dosonthepi.blogspot.co.uk/2015/01/run-dos-games-in-retropie_15.html#add-dosgames)

[How to configure DOSBOX for individual games.](http://dosonthepi.blogspot.co.uk/2015/02/dosbox-configuration-for-individual.html)
**aka one .conf file per game. Recommended way to add games in order to keep a clean setup and ease debug process (whenever needed).**

[How to configure USB game controllers in DOSBox.](http://dosonthepi.blogspot.co.uk/2015/01/configure-game-controllers-in-dosbox_29.html)

[How to create a default (arcade) mapping for game controllers in DOSBox.](http://dosonthepi.blogspot.co.uk/2015/02/default-arcade-mapping-for-dosbox.html)

[Update for Retropie 3.0.](http://dosonthepi.blogspot.co.uk/2015/04/retropie-30-update.html)

[**DosBOX Compatibility List**](https://docs.google.com/spreadsheets/d/1Tx5k3F0_AO6w00WrXULMBSUTRhtLyIhHI8Wz8GuqLfQ/edit?usp=sharing) feel free to contribute to the list. 

see also forum post [here](http://blog.petrockblock.com/forums/topic/resource-dosbox-compatibility-list/)

## DOS/32A extender
As per Dosbox' documentation: [DOS/32A (DOS/32 Advanced DOS Extender)](https://dos32a.narechk.net/index_en.html) is a free and open source software that can be used to replace the DOS4GW.EXE DOS Extender file that many DOS games use. Once a game uses this, it is expected to run faster and better in DOSBox. 

**Note**: **_not all games will work with DOS/32A_**. For example, Shadowcaster is incompatible with it because RAVEN.EXE run with DOS/32A is unable to find the A32SBDG.DLL file that is in the same directory, while with DOS4GW it can. 

[**DOS/32A compatibility list**](https://github.com/dosbox-staging/dosbox-staging/wiki/DOS32A-compatibility-list)

Check [Dosbox' documentation](https://www.dosbox.com/wiki/TOOLS:DOS32A) to get further information as well as a guide on how to proceed.

Once "patched" your file executable should look like this:
```
$ file hospital.exe
MS-DOS executable, LE executable for MS-DOS, DOS/32A DOS extender (embedded)
```

## Install Gravis Ultrasound (GUS)
DOSBox comes with **Gravis Ultrasound** support, but you need a little effort to set it up. It's worth it definitely as the difference with a SoundBlaster 16 is impressive (check that for yourself with a game like Rise of the Triad, it's night and day).
1. You must first find the GUS driver for Dosbox. As I'm not 100% sure about the legality of the file no link can be shared from this wiki. 
2. If you get the file it should typically be containing a "ULTRASND" folder with various files and folders within.
3. Simply copy that "ULTRASND" folder straight under your Retropie "roms" directory for Dosbox (default: roms/pc).
4. Edit the .conf of your game(s) and get to the `[gus]` section. Modify it this way:
```
[gus]
[...]
gus      = true
gusrate  = 44100
gusbase  = 240
gusirq   = 5
gusdma   = 3
ultradir = C:\ULTRASND
```
5. All left to do is to **configure the game with GUS as the soundcard for music and digital effects**. You can do that usually via `setup.exe` or `install.exe` located in your game's directory.
Note: it's ok to move the "ULTRASND" directory to another location. Just remember to "mount" it whenever you launch the game.

[List of DOS games with GUS support](https://www.mobygames.com/attribute/sheet/attributeId,20/).

## Tips
With DOSbox on a **Pi3B+** without overclocking (stock) I was able to get up to **34000 cycles**. Meaning a solid equivalent of a good 486DX2 or even Pentium 60 (according to [this page](https://www.dosbox.com/wiki/Performance)). Below the `cpu` setting I'm currently using for the majority of games ([DOSbox' doc](https://www.dosbox.com/wiki/Configuration:CPU)).
```
[cpu]
cycles = max 95% limit 34000
```

Whenever a game is running **too fast** you'll have to rely on the `fixed` parameter of `cycles`. Good example with Wing Commander (1 and 2):
```
[cpu]
cycles = fixed 4000
```

## Troubleshooting

If the keyboard input in DOSBox is not correct, you need to edit the DOSBox config file, dosbox-SVN.conf, which is located in the hidden folder, .dosbox, in your home folder.

To fix, run the following commands:

    cd ~/.dosbox
    sudo nano dosbox-SVN.conf

In the [sdl] section, edit line 34 of dosbox-SVN.conf so that usescancodes is set to false as below:

    usescancodes=false

In some games your joystick/controller may be permanently fixed in one corner. For these games, edit dosbox-SVN.conf, find the [Joystick] section and set timed to false as below:

    timed=false

rpix86 defaults to analog audio output, if you use HDMI audio you need to give -a0 parameter to rpix86