If you add

    input_exit_emulator_btn = "btn#"

to your retroarch.cfg you will be able to exit the emulator on a button press. I know of no way to do this with multiple buttons. Here, btn# has to be replaces by your desired button number on your gamepad/joystick.

The following comes from [here](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=250689#p250689):

> To anyone trying to set up an exit button for RetroArch on an authentic controller, a solution has been found: http://forum.themaister.net/viewtopic.php?pid=1065#p1065

> The idea is to set a key that must be held to use hot keys (such as select) with "input_enable_hotkey_btn = 1" and then an exit key (such as start), which will now only work if the enable hot key button is held down, with "input_exit_emulator_btn = 2".

> Thanks to MungoBBQ for pointing this out!
