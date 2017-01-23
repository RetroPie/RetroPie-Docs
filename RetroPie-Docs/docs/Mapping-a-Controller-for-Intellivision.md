To map a controller in jzintv, you need to create a Keyboard Hack File which is a text file that contains the mappings. This is a dirty fix meaning that you will have to manually create and edit text files on your pi. It would be useful that you are familiar with using SFTP and Samba shares for accessing files on your pi. Details can be found at the [wiki](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#sftp-needs-an-active-internet-connection).

## Find Joystick Events

To find the events sent by your joystick to jzintv, you need to run `event_diag.rom`. You can download it from [here](http://atariage.com/forums/index.php?app=core&module=attach&section=attach&attach_id=139949).

Place event_diag.rom in your intellivision rom folder and from a terminal on your pi, run the following command:

    /opt/retropie/emulators/jzintv/bin/jzintv -p /home/pi/RetroPie/BIOS -q /home/pi/RetroPie/roms/intellivision/event_diag.rom

Now press buttons or move the left analog stick and you will see how jzintv reads the input.

Below is the output using a PS3 controller when pressing the X button (`JS0_BTN_14`), right on the D-pad (`JS0_BTN_05`) and pushing the left analog stick right (`JS0_E`), then left (`JS0_W`).

![](https://cloud.githubusercontent.com/assets/8166945/18489597/0fa80946-79f6-11e6-8881-476896f42796.png)

Make a note of these bindings as they will be used in creating the keyboard hack file.

## Mappings in a Keyboard Hack File

To create a keyboard hack file, it is a case of taking each joystick event and mapping it to the appropriate INTV controller input. The latter is detailed in the [official documentation](http://spatula-city.org/~im14u2c/intv/jzintv-1.0-beta3/doc/jzintv/kbdhackfile.txt) and the relevant section is given below:

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

An sample keyboard hack file would be:

<pre>; -----------------------------------------------------------------------------------------
MAP 0      ; keymap 0 (default keymap)
; -----------------------------------------------------------------------------------------

; ***** Joystick #0 - Left Controller *****
; ** Side Buttons and Numeric Keypad **
JS0_BTN_00 PD0L_A_T
JS0_BTN_01 PD0L_A_L
JS0_BTN_02 PD0L_A_R
JS0_BTN_03 PD0L_KP1
JS0_BTN_04 PD0L_KP2
JS0_BTN_05 PD0L_KP3
JS0_BTN_06 PD0L_KP4
JS0_BTN_07 PD0L_KP5
JS0_BTN_08 PD0L_KP6
JS0_BTN_09 PD0L_KP7
JS0_BTN_10 PD0L_KP8
JS0_BTN_11 PD0L_KP9
JS0_BTN_12 PD0L_KPC
JS0_BTN_13 PD0L_KP0
JS0_BTN_14 PD0L_KPE


; ** Direction Disc **
JS0_N      PD0L_J_N
JS0_NNE    PD0L_J_NNE
JS0_NE     PD0L_J_NE
JS0_ENE    PD0L_J_ENE
JS0_E      PD0L_J_E
JS0_ESE    PD0L_J_ESE
JS0_SE     PD0L_J_SE
JS0_SSE    PD0L_J_SSE
JS0_S      PD0L_J_S
JS0_SSW    PD0L_J_SSW
JS0_SW     PD0L_J_SW
JS0_WSW    PD0L_J_WSW
JS0_W      PD0L_J_W
JS0_WNW    PD0L_J_WNW
JS0_NW     PD0L_J_NW
JS0_NNW    PD0L_J_NNW

; ***** Joystick #1 - Right Controller *****
; ** Side Buttons and Numeric Keypad **
JS1_BTN_00 PD0R_A_T
JS1_BTN_01 PD0R_A_L
JS1_BTN_02 PD0R_A_R
JS1_BTN_03 PD0R_KP1
JS1_BTN_04 PD0R_KP2
JS1_BTN_05 PD0R_KP3
JS1_BTN_06 PD0R_KP4
JS1_BTN_07 PD0R_KP5
JS1_BTN_08 PD0R_KP6
JS1_BTN_09 PD0R_KP7
JS1_BTN_10 PD0R_KP8
JS1_BTN_11 PD0R_KP9
JS1_BTN_12 PD0R_KPC
JS1_BTN_13 PD0R_KP0
JS1_BTN_14 PD0R_KPE


; ** Direction Disc **
JS1_N      PD0R_J_N
JS1_NNE    PD0R_J_NNE
JS1_NE     PD0R_J_NE
JS1_ENE    PD0R_J_ENE
JS1_E      PD0R_J_E
JS1_ESE    PD0R_J_ESE
JS1_SE     PD0R_J_SE
JS1_SSE    PD0R_J_SSE
JS1_S      PD0R_J_S
JS1_SSW    PD0R_J_SSW
JS1_SW     PD0R_J_SW
JS1_WSW    PD0R_J_WSW
JS1_W      PD0R_J_W
JS1_WNW    PD0R_J_WNW
JS1_NW     PD0R_J_NW
JS1_NNW    PD0R_J_NNW
</pre>

This hack file will map every input available. For the left controller, you may wish to include only the input(s) you wish to remap. For example, if your gamepad has an analog stick, you can remove the Direction Disc mappings.

For the right controller, it is advised that every input is mapped as this is not done by default.

Once amended to suit, save the keyboard hack file as `hackfile.cfg` in your Intellivision roms folder.

###Configuring jzIntv

To use the keyboard hack file, you need to add the `--kbdhackfile` flag when launching jzIntv.

Amend the line in `/opt/retropie/configs/intellivision/emulators.cfg` to launch jzIntv to :

    jzintv = "/opt/retropie/emulators/jzintv/bin/jzintv -p /home/pi/RetroPie/BIOS -q --kbdhackfile=/home/pi/RetroPie/roms/intellivision/hackfile.cfg %ROM%"