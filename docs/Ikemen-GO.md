***

![ikemen-logo](https://user-images.githubusercontent.com/22881403/129746968-af1896d1-4276-4943-981d-b68bbd3eab21.png)

***
_I.K.E.M.E.N GO is an open-source implementation of the M.U.G.E.N fighting game engine, originally developed by Elecbyte in 1999, written using the Go programming language.  I.K.E.M.E.N GO adds many additional features and bug fixes in addition to being backwards compatiable with content created for M.U.G.E.N._
***

## Ports: [I.K.E.M.E.N GO](https://github.com/Windblade-GR01/Ikemen-GO)
As a general rule of thumb, tutorials made for M.U.G.E.N will largely apply to I.K.E.M.E.N GO as well, with only minor differences.  For additional information about configuring the engine, see [Elecbyte's M.U.G.E.N documentation](http://www.elecbyte.com/mugendocs/readme.txt) and the various guides and tutorials around the internet for both M.U.G.E.N and I.K.E.M.E.N GO.

For more information on features specific to I.K.E.M.E.N GO, see [the I.K.E.M.E.N GO documentation.](https://github.com/K4thos/Ikemen_GO/wiki)

## ROMs
Place your M.U.G.E.N / I.K.E.M.E.N content in:
```
/home/pi/RetroPie/roms/ports/ikemen-go/
```

A typical file structure should look like this:
```
ikemen-go
|-- chars
|    |    (character folders should be placed here,
|    |    ideally containing a .def file with the
|    |    same name as the folder that contains it)
|    |
|    + -- kfm
|         | -- kfm.def
|         | -- kfm.sff
|         | -- kfm.snd
|         | -- kfm.cns
|         | -- kfm.cmd
|         + -- (etc.)
|
|-- stages
|    |    (stage files should be placed here, typically
|    |    they come with a .def, a .sff, and an audio file
|    |    that must be placed in the sound folder)
|    |
|    | -- stage0.def
|    + -- stage0.sff
|
|-- data
|    |    (screenpack / motif folders should be placed here)
|    |
|    | -- system.def
|    | -- select.def (edit this to add characters/stages)
|    | -- fight.def
|    + -- (etc.)
|
|-- external
|    | -- icons
|    | -- mods (place additional LUA scripts here)
|    | -- script
|    + -- shaders (place GLSL shaders here)
|
|-- font
|    |    (additional fonts should be placed here, some motifs
|    |    might keep their fonts in their own folders however)
|    |
|    | -- default-3.5x.def
|    | -- default-3.5x.sff
|    | -- f-4x6.fnt
|    + -- (etc.)
|
+-- sound
     | -- (optional stage audio files go here,
     + -- currently MP3 and OGG are accepted)
```

### Characters
Characters consist of several files stored in a folder.  The contents of the character's folder usually looks something like this:
```
kfm
| -- kfm.def    (definitions file; ideally named after the folder itself)
| -- kfm.sff    (sprites file; may also contain palettes)
| -- kfm.snd    (sound file)
| -- kfm.cns    (code file)
| -- kfm.cmd    (input commands file)
| -- kfm1.act   (color palette file; up to 12 for a single character)
| -- kfm2.act
| -- kfm3.act
+ -- etc.
```
The folder should be placed in this directory:
```
/home/pi/RetroPie/roms/ports/ikemen-go/chars
```
### Stages
Stages consist of at least two files: a .def file and a .sff file.  There may also be an additional .air file for storing animation data.  Stage files should be placed into the following directory:
```
/home/pi/RetroPie/roms/ports/ikemen-go/stages
```

Stages often contain a file for music, either in MP3 or OGG format.  These must be placed in a separate directory:
```
/home/pi/RetroPie/roms/ports/ikemen-go/sound
```

### Screenpacks / Motifs
The installation process will vary on a per-screenpack basis, but generally their files should be placed in:
```
/home/pi/RetroPie/roms/ports/ikemen-go/data
```

To use the newly-installed screenpack, you must point to the screenpack's `system.def` file by editing the following file:
```
/opt/retropie/configs/ports/ikemen-go/save/config.json
```

Edit the file path in this line to point to your screenpack's `system.def` file:
```json
	"Motif": "data/system.def",
```

### Adding to the roster
Once the character folders and/or stage files are placed in the proper directories, the following file must be edited in order for them to show up on the character and stage select screen:
```
/home/pi/RetroPie/roms/ports/ikemen-go/data/select.def
```

The file contains a list of all the characters and stages, listed with either a folder name or a path to a .def file.  Characters must be listed under the section named `[Characters]`, and stages can be listed either next to a particular character (separated with a comma) or under the `[ExtraStages]` section.  You can also add `randomselect` to add a random slot to the roster.

Following the character declaration, you can also add a specific stage to associate with the character, as well as extra parameters.  The characters will be displayed on the character select screen from left to right, top to bottom, in chronological order according to this file.
```ini
[Characters]
kfm
kfm720/kfm720.def, stages/stage0-720.def
randomselect

[ExtraStages]
stages/stage0.def
stages/kfm.def
```

See the comments in select.def for more information about extra parameters.

## Controls

Controls can be configured in-game by going to **Options -> Input Settings -> Key Config / Joystick Config -> Config All**, and are located in:

```
/opt/retropie/configs/ports/ikemen-go/save/config.json
```

### Default controls
|Key|Action|
|---|---|
|ESC|Pause / Back|
|Left/Right Arrow|Move left/right|
|Up Arrow|Jump|
|Down Arrow|Crouch|
|Z|A Button|
|X|B Button|
|C|C Button|
|A|X Button|
|S|Y Button|
|D|Z Button|
|Enter/Return|Start|
|F12|Take Screenshot|

Note that control schemes can vary wildly on a per-character basis.  For more information, see the included readme files or other documentation with your specific characters.

## Configs

Options can be configured in-game via the **Options** menu.  A default configuration file is generated upon first run, located in:
```
/opt/retropie/configs/ports/ikemen-go/save/config.json
```

## Issues
### Performance
Performance can vary greatly depending on a number of factors, such as the clockspeed of your CPU and GPU, the specific characters and stages you're using, whether you're playing Single, Simul, Tag, or Team matches, and many others.  

I.K.E.M.E.N GO is also rather RAM-hungry; a Raspberry Pi 4 with 4GB of RAM is recommended if you plan to have lots of content loaded in a single roster; loading too many characters in a single session or loading lots of characters with large file sizes can result in I.K.E.M.E.N GO freezing due to running out of RAM.

### Crash on Composite Out
When attempting to run I.K.E.M.E.N GO on the Pi's composite out, the game may crash on startup.  To fix this crash, set **Fullscreen** to false, either by launching the game on HDMI out and going to the options menu or by manually editing `config.json`:
```json
	"Fullscreen": false,
```
