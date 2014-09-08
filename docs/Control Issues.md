Control Issues
==============

Configuring SNES controls for the Emulationstation
--------------------------------------------------
Whenever you hook up the SNES controllers the controllers will work within the operating system. 
Tho since the RetroArch is configurered seperately the controls need to be set also for each emulator. 
in the folders ~/Retropie/configs/* all "retroarch.cfg" files can be modified seperately for each emulator. Whenever you want to make global changes edit the retroarch.cfg in the ~/Retropie/configs/all.

Setting up a controller is fairly easy.
navigate to ~/Retropie/emulators/Retroarch/tools/
Type in : retroarch-joyconfig -o ~/Retropie/configs/all/retroarch.cfg 
\\
the -o argument will output the config directly into a cfg file for all emulators. In case you don't want this remove everything after the -o and only use the retroarch-joyconfig command
\\

During the setting up of the config lots of questions may arise for which you have no button ( L3 buttons do not exist on a SNES controller for instance ) just press one of the random buttons. 

After the configuring has been done, 
type: nano ~/Retropie/configs/all/retroarch.cfg
Read all the lines stated there. Delete all the lines that are describing axes, L3 buttons etc. 
then save the file ( ctrl-X )

-- For setting up a Player 2
Copy copy the content of the retroarch.cfg and paste it in the same file.
change the index of the first "set of controls" to index"1"
Now if you did this properly you have a entry for all the controls of a joystick with index "1" and a joystick index "0".

-Webrow

Setting Up an USB joystick/gamepad 
----------------------------------
RetroArch is configured for joystick hotplug and auto configuration. If your joystick/gamepad does not work out of the box, run the following command to create an auto configuration file for your joystick/gamepad. 
 
/opt/retropie/emulators/RetroArch/installdir/bin/retroarch-joyconfig -a /opt/retropie/emulators/RetroArch/configs/gamepad.cfg

Setting Up an USB DGEN joystick/gamepad
----------------------------------

1.  go to ~~/RetroPie/configs/all/

2.  sudo nano dgenrc

and uncomment the joystick lines. Putting your own button numbers corresponding to your joystick / gamepad.

Setting Up a Bluetooth Controller
---------------------------------

You can find a nice tutorial about setting up a bluetooth controller at http://mypiandi.blogspot.de/2012/12/retropie-sixaxis-over-bluetooth.html.

GameGear and MasterSystem Keyboard Input
----------------------------------------

If you want to use the keyboard as input for these systems you need to remove the parameter "-joy" from the call of Osmose in the file ~/.emulationstation/es_systems.cfg.