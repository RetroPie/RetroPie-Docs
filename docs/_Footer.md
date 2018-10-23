----
**The RetroPie Project**

[About](https://retropie.org.uk/)  | [Forum](https://retropie.org.uk/forum/)   |  [Setup-Script](https://github.com/RetroPie/RetroPie-Setup)
--------|----------|---------


Everything has changed in the later release of RetroPie

All this is different and can't find

Now we will recreate this using the retroarch controller script, type
sudo /home/pi/RetroPie-Setup/retropie_setup.sh

-----> Please update correct instructions..
Choose the "Setup" option, then "Configure input devices for RetroArch" (Do not choose the "Install RetroArch joypad autoconfigs)
Then choose the "Configure joystick/controller for use with RetroArch" option
Follow the on-screen prompts to press the buttons when prompted.
If you make a mistake, just run it again, it happily overwrites the file it needs to.

There should be no need to edit the retroarch.cfg to get your controller working.

That should be all you need. Now when you start your Pi, set the controller to connect and it should be detected by Emulation Station and RetroArch based emulators.