Here come the frequently asked questions

### Why do some emulators not show up?

In Emulation Station, only emulators with ROMs inside its respective folder will show up in the Emulation Station GUI (given that the specific emulator is installed). For example, for the Nintendo 64 emulator to show up, you must have at least one ROM in the `~/RetroPie/roms/n64/` folder. For ROM types supported by each emulator, go to the wiki page for that specific system/emulator. 

### Why Can't I Insert Coins in Arcade Emulators?

It's the Select button in RetroArch. By default, it's right shift.

Sometimes there are conflicts between the hotkeys and insert coin buttons so they need to be swapped manually in the retroarch.cfg in order for the select key to insert coins properly. The hotkey button was originally intended to be an unused button but some controllers like snes controllers don't have extra buttons.

For example you can switch the hotkey button to a button that you don't use:

so in mame retroarch.cfg
```
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```

you could add 
```
input_enable_hotkey_btn = 5
```
which would make the hotkey the left bumper (on my controller- may be a different button for yours) then the select key should work for inserting coins. but in the future in order to exit mame I would then have to press left bumper+start as i changed my hotkey to the left bumper. 

You can do the same thing for fba-libretro
```
/opt/retropie/configs/fba/retroarch.cfg
```

Another simple workaround is to use player 2's select key to insert coins but it may not work for some games.

Related post  
http://blog.petrockblock.com/forums/topic/fba-retroarch-core-coin-controls/#post-93014

### Why can't I SSH as root anymore?

Starting with RetroPie 3.0 BETA 3 the root password was disabled (as is the case for Raspbian by default and many other linux distros). 

If you would like to re-enable root access, in the terminal type:

```shell
sudo passwd root
```

see these posts for more details:

https://www.raspberrypi.org/documentation/linux/usage/root.md

http://elinux.org/R-Pi_Troubleshooting#I_don.27t_know_the_root_password


**RetroPie 3.0 Jessie Builds:**

before setting a root password, the following must be edited

```sudo nano /etc/ssh/sshd_config```

look for 

```PermitRootLogin without-password```

change it to

```PermitRootLogin yes```

then ctrl+x to save, next set your root password & restart your Pi

### Where did the desktop go?

The LXDE desktop environment was removed from the RetroPie image to keep it smaller. You can install it with

`sudo apt-get install lxde`

For Raspbian Jessie you also need to install:

`sudo apt-get install xinit`

And then you can access it from the terminal by typing in

`startx`

After installation your pi will boot into the desktop environment, you can change the behaviour to boot into emulationstation by selecting the autostart option for emulationstation from option 3 of the setup script, or you can set the autologin to console option from the boot options of the raspi-config menu.

### Does anybody know if there's a way to edit the retroarch.cfg to give me the ability to exit an emulator by using the controller?

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

### Does Super Mario All Stars work?

The ROM does work with PocketSnes (RetroArch) only.

From http://blog.petrockblock.com/2012/07/22/retropie-setup-an-initialization-script-for-retroarch-on-the-raspberry-pi/#comment-818063235:

> I found out that after the selection of a game, the control goes over to the second controller! This seems to be somehow a speciality of the All-Stars ROM. But at least, it is playable :-)

Alternatively, if you only have one controller (or play alone) you can do the following:

From http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=79083

> I managed to figure out a fix so the controls work in Super Mario All-Stars and also doesn't break other games (Mario Kart, Super Bomberman etc). This problem has been bugging me for ages and I had to figure out a way to play this game for nostalgia sake. This fix will unfortunately mean player two controls wont work for other games (but I play alone anyway and this is for people with one controller). Simply post this in your blank retroarch.cfg in the snes folder. P.S Remember to change the button numbers/axis for you own controller.

### How do I extend the available space when upgrading to a larger SD card

1. Navigate to the command line interface by either hitting F4 in EmulationStation or using the main menu to exit
1. Type in the following command: `sudo raspi-config`

1. Select option "1. Expand Filesystem"
1. Reboot your Raspberry Pi

### How would I start from command line, say, the SNES emulator by itself?

You can run a SNES rom by calling 

```
retroarch -L /opt/retropie/libretrocores/lr-pocketsnes/libretro.so /home/pi/RetroPie/roms/snes/nameofyourrom.smc
```

If you'd like keyboard configurations to work add
```
--config /opt/retropie/configs/all/retroarch.cfg
```

### Is there another way to set up the gamepad for use, e.g., within the snes emulator?

Follow the RetroArch-Configuration guide:

https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration

### The PSX emulator reports no BIOS found. What do I do?

Ensure the bios file(s) is/are all lowercase and put them in
```shell
/home/pi/RetroPie/BIOS
```

More information about PSX BIOS files can be found on the [PSX page](https://github.com/petrockblog/RetroPie-Setup/wiki/Playstation-1).

### Which memory split should I use?

Using the raspi-config or rpi-update script, one can change the RAM splitting for the Raspberry Pi. Depending on your hardware setup you might have to change your splitting.

From [ToadKing](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=112241#p112241):
> If you're on 224/32, you can't run it (i.e., RetroArch) on a HD display. You'll have to use the 192/64 split at least.

A Raspberry Pi B/B+/2 is highly recommended. The GPU should have at least 256MB RAM. If you have a Raspberry Pi A/A+  it is not possible to scrape games and use system themes. 

