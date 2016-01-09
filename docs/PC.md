***
![ibmpc](https://cloud.githubusercontent.com/assets/10035308/12213490/0f8cb422-b636-11e5-99a7-2a33761874f3.png)
***
_The good old days of DOS._
***
## Emulator: [DOSBox](http://www.dosbox.com/), [Rpix86](http://rpix86.patrickaalto.com/)

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

[**DosBOX Compatibility List**](https://docs.google.com/spreadsheets/d/1Tx5k3F0_AO6w00WrXULMBSUTRhtLyIhHI8Wz8GuqLfQ/edit?usp=sharing) feel free to contribute to the list. 

see also forum post [here](http://blog.petrockblock.com/forums/topic/resource-dosbox-compatibility-list/)

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