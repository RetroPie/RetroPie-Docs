If you add

    input_exit_emulator_btn = "btn#"

to your retroarch.cfg (opt/retropie/configs/all) you will be able to exit the emulator on a button press. I know of no way to do this with multiple buttons. Here, btn# has to be replaced by your desired button number on your gamepad/joystick and the quote marks need to be removed. So the actual command might be:

    input_exit_emulator_btn = 9

(For the L3 button on your xbox controller, in this example)

But this wasn't enough for my configuration to work. I also had to do these three commands:

    sudo chown pi /opt/retropie/configs/all/retroarch.cfg
    cd /opt/retropie/emulators/RetroArch/installdir/bin
    sudo ./retroarch-joyconfig -j 0 >> /opt/retropie/configs/all/retroarch.cfg

Which then directs you to input all the buttons required. Keep a note of the numbers of the buttons, in case you want to use a particular number for the input_exit_emulator_btn command. What then happens is this button configuration is stored in retroarch.cfg. Only then did the exit emulator button command work for me. Also, it's tempting to use button 8 (the xbox button) to exit emulators, but since it's not asked for/configured by the retroarch-joyconfig program it won't do anything if you add it to the config, I don't think. ymmv. Hope this has been helpful. This took me 3 hours, but I'm not very linux-minded.

The following comes from [here](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=250689#p250689):

> To anyone trying to set up an exit button for RetroArch on an authentic controller, a solution has been found: http://forum.themaister.net/viewtopic.php?pid=1065#p1065

> The idea is to set a key that must be held to use hot keys (such as select) with "input_enable_hotkey_btn = 1" and then an exit key (such as start), which will now only work if the enable hot key button is held down, with "input_exit_emulator_btn = 2".

> Thanks to MungoBBQ for pointing this out!

**Constraint**: This doesn't work for gpsp.

I recently had to set this up myself on my pi, and wanted to add a few things:
First, for a generic PS3 type controller the "PS" button in the center of the controller is button 12, so to exit a game with a simple button push, go to the bottom of your retroarch.cfg file and add the following line,
           `input_exit_emulator_btn = 12`
and when you press the PS button, your game will exit gracefully to the main Emulation Station screen.
Second, the following line: 
            `sudo ./retroarch-joyconfig -j 0 >> /opt/retropie/configs/all/retroarch.cfg`
will automatically define the button settings for the first controller plugged in (Controller / joystick 0) and append the settings to your retroarch.cfg file. If you screw up during the mapping it's not a big deal, just remember that with the double greater than >> every time you run the command the settings will be appended to the pre-existing settings you had. Easiest way to do this is to use an editor like nano to delete the last few lines in retroarch.cfg that apply to your controller, then re-run the joyconfig script to remap.

In order to get the xbox home button working as the exit emulator button, I added the following lines to the very end of the retroarch.cfg file, below the button mappings for each controller.
        
        input_enable_hotkey_btn = "10"
        input_exit_emulator_btn = "10"

The first line sets a hotkey button, which was mapped to the home button. The second line sets which button is used as the "exit emulation" hotkey, however, since we matched it to the home button as well, it automatically exits out back to Emulation Station.