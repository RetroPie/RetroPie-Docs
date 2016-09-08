To map a controller in jzintv, you need to create a Keyboard Hack File which is a text file that contains the mappings. This is a dirty fix meaning that you will have to manually create and edit text files on your pi. It would be useful that you are familiar with using SFTP and Samba shares for accessing files on your pi. Details can be found at the [wiki](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#sftp-needs-an-active-internet-connection).

## Find Joystick Events

To find the events sent by your joystick to jzintv, you need to run event_diag.rom. You can download it from [here](http://atariage.com/forums/index.php?app=core&module=attach&section=attach&attach_id=139949).

[If you know the joystick numbers of your controller from using jstest, then you can skip the next section as the buttons assignments are identical.]

Place event_diag.rom in your intellivision rom folder and from a terminal on your pi, run the following command:

    /opt/retropie/emulators/jzintv/bin/jzintv /home/pi/RetroPie/roms/intellivision/event_diag.rom

Now press buttons or move the left analog stick and you will see how jzintv reads the input.

Below is the output using a PS3 controller when pressing the X button (`JS0_BTN_14`), right on the D-pad (`JS0_BTN_05`) and pushing the left analog stick right (`JS0_E`), then left (`JS0_W`).

![](https://lh3.googleusercontent.com/pbprnfBlQaolkPlfRtZcfZmkZemYSfRESVqYGTW7n_10Be0QUMwWOXDdaJZMrJ1DGPLuzkIn=w1254-h805)

Make a note of these bindings as they will be used in creating the keyboard hack file.

## Mappings in a Keyboard Hack File

To create a keyboard hack file, it is a case of taking each joystick event and mapping it to the appropriate INTV controller input. The latter is detailed in [official documentation](http://spatula-city.org/~im14u2c/intv/jzintv-1.0-beta3/doc/jzintv/kbdhackfile.txt) and the relevant section is given below:

<pre>
Controller inputs start with one of the following four prefixes:
 
PD0L_   Left controller, Master Component
PD0R_   Right controller, Master Component
PD1L_   Left controller, ECS
PD1R_   Right controller, ECS

Those four prefixes get combined with these suffixes:
 
KPx     Keypad key.  x=0,1,2,3,4,5,6,7,8,9,C,E
A_x     Action key.  x=T,L,R
D_ddd   Disc input.  ddd=E,ENE,NE,NNE,N,NNW,NW,WNW,W,WSW,SW,SSW,S,SSE,SE,ESE
J_ddd   Disc input from joystick.  ddd same as above.
</pre>
Below are example mappings.

1. To map the Start button on a PS3 controller to the Enter key on the left Intellivision controller, it would be a case of mapping **JS0_BTN_03** to **PD0L_KPE**.
2. To map the X button on a PS3 controller to the top side action button, it would be a case of mapping **JS0_BTN_14** to **PD0L_A_T**.
3. To map the X button on a second PS3 controller to the top side action button on right Intellivision controller, it would be a case of mapping **JS1_BTN_14** (JS1_ represents the second controller) to **PD0R_A_T** (PD0R_ represents the right Intellivision controller).

Each keyboard hack file will have a first line of `MAP 0` to denote the default keymap in jzintv.

For each joystick mapping, you will need to add a line mapping the joystick event to the INTV controller input. Comments can be added by including a semi-colon at the beginning of a line.

Using the examples above, a sample keyboard hack file would be:

    
    MAP 0

    ; Sample keyboard hack file
    JS0_BTN_03 PD0L_KPE
    JS0_BTN_14 PD0L_A_T
    JS1_BTN_14 PD0R_A_T

## The Arcade Mapping

This keyboard hack file is an "arcade" mapping that will cover most games that require movement and one or two buttons to fire or jump. The hack file will also allow to set game difficulty and enter the number of players.

In the intellivision roms folder, create a text file and call it **Arcade.kbd**. Add the lines below, amending as necessary, and save.

####Example keyboard hack file for a PS3 controller.

    MAP 0

    ; Game interface

    JS0_BTN_00 QUIT
    JS0_BTN_16 RESET

    ; Keypad

    JS0_BTN_04 PD0L_KP1
    JS0_BTN_05 PD0L_KP2
    JS0_BTN_06 PD0L_KP3
    JS0_BTN_07 PD0L_KP4
    JS0_BTN_03 PD0L_KPE
    JS0_BTN_12 PD0L_KP0
    JS0_BTN_13 PD0L_KPC

    ; Action Side Button
    JS0_BTN_14 PD0L_A_T
    JS0_BTN_15 PD0L_A_L

###Configuring jzintv

To use the keyboard hack files, you need to add the `--kbdhackfile` flag when launching jzintv.

Add the following line to `/opt/retropie/configs/intellivision/emulators.cfg`:

    jzintv-arcade = "/opt/retropie/emulators/jzintv/bin/jzintv -p /home/pi/RetroPie/BIOS -q --kbdhackfile=/home/pi/RetroPie/roms/intellivision/Arcade.kbd %ROM%"

For good measure to make sure all roms will launch with the arcade mapping, you can set the default in emulators.cfg to "jzintv-arcade".



## The Bespoke Mapping

A bespoke mapping will vary from game to game, from controller to controller. The arcade mapping can be used as a starting point.

_[Coming soon]_