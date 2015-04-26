![IBM Logo](http://upload.wikimedia.org/wikipedia/commons/thumb/5/51/IBM_logo.svg/320px-IBM_logo.svg.png)
***
_The good old days of DOS._
***
## Emulator: [DOSBox](http://www.dosbox.com/)

## ROMS
Accepted File Extensions: **.com .sh .bat .exe**

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

[How to configure USB game controllers in DOSBox.](http://dosonthepi.blogspot.co.uk/2015/01/configure-game-controllers-in-dosbox_29.html)

[How to create a default (arcade) mapping for game controllers in DOSBox.](http://dosonthepi.blogspot.co.uk/2015/02/default-arcade-mapping-for-dosbox.html)

[How to configure DOSBOX for individual games.](http://dosonthepi.blogspot.co.uk/2015/02/dosbox-configuration-for-individual.html)

[Update for Retropie 3.0.](http://dosonthepi.blogspot.co.uk/2015/04/retropie-30-update.html)

## Troubleshooting

If the keyboard input in DOSBox is not correct, you need to edit the DOSBox config file, dosbox-SVN.conf, which is located in the hidden folder, .dosbox, in your home folder.

To fix, run the following commands:

    cd ~/.dosbox
    sudo nano dosbox-SVN.conf

In the [sdl] section, edit line 34 of dosbox-SVN.conf so that usescancodes is set to false as below:

    usescancodes=false
