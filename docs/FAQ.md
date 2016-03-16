- [Why do some emulators not show up?](https://github.com/retropie/RetroPie-Setup/wiki/FAQ#why-do-some-emulators-not-show-up)
- [Why Can't I Insert Coins in Arcade Emulators?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-insert-coins-in-arcade-emulators)
- [Why can't I SSH as root anymore?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#why-cant-i-ssh-as-root-anymore)
- [Where did the desktop go?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#where-did-the-desktop-go)
- [How do I change which buttons to press to exit an emulator with a controller?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-change-which-buttons-to-press-to-exit-an-emulator-with-a-controller)
- [Does Super Mario All Stars work?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#does-super-mario-all-stars-work)
- [How do I extend the available space when upgrading to a larger SD card](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-extend-the-available-space-when-upgrading-to-a-larger-sd-card)
- [How would I start from command line, say, the SNES emulator by itself?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-would-i-start-from-command-line-say-the-snes-emulator-by-itself)
- [Is there another way to set up the gamepad for use, e.g., within the snes emulator?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#is-there-another-way-to-set-up-the-gamepad-for-use-eg-within-the-snes-emulator)
- [The PSX emulator reports no BIOS found. What do I do?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#the-psx-emulator-reports-no-bios-found-what-do-i-do)
- [Which memory split should I use?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#which-memory-split-should-i-use)
- [How do I hide the boot text?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#how-do-i-hide-the-boot-text)
- [Why does shutting down/booting/restarting EmulationStation take ages?](https://github.com/RetroPie/RetroPie-Setup/wiki/FAQ#Why-does-shut-down-and-reboot-take-ages)

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

### How do I change which buttons to press to exit an emulator with a controller?

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games. The following defaults are set automatically the first time you set up your controller from emulationstation.

#### Default joypad hotkeys:
Hotkeys | Action | Code Example
| :---: | :---: | :---: |
Select | Hotkey | input_enable_hotkey_btn = "6"
Select+Start | Exit | input_exit_emulator_btn = "7"
Select+Right Shoulder | Save | input_save_state_btn = "5"
Select+Left Shoulder | Load | input_load_state_btn = "4"
Select+Right | Input State Slot Increase | input_state_slot_increase_btn = "h0right"
Select+Left | Input State Slot Decrease | input_state_slot_decrease_btn = "h0left"
Select+X | RGUI Menu | input_menu_toggle_btn = "3"
Select+B | Reset | input_reset_btn = "0"

You can adapt the above code example and choose the button number to your desired button for each hotkey function in the retroarch.cfg files for most systems (at least all the emulators that are part of RetroArch) 

You can change it per controller with your autoconfig file here 

```
/opt/retropie/configs/all/retroarch-joypads/yourgamepad.cfg
```

You can Hardcode it globally for all systems here:

```
/opt/retropie/configs/all/retroarch.cfg 
```

or set it by system

```
/opt/retropie/configs/SYSTEMNAME/retroarch.cfg
```

See [HERE](RetroArch-Configuration) for more information on custom controller configs

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

### How do I hide the boot text?

**NOTE that you should be comfortable with editing files in Linux as any wrong edits on the following file can break your boot sequence requiring a reimage of your SD card!**

`sudo nano /boot/cmdline.txt`

change `console=tty1` to `console=tty3` 

And add `quiet loglevel=3 logo.nologo` at the end.

**make sure it is all on the same line!!!** 

The logo.nologo option is what turns off the raspberries on boot.

You can also disable the rainbow splash at the beginning (not to be confused with the underpowered rainbow square the appears in the top right corner of your screen indicating you have an insufficient power supply)

Add `disable_splash=1` in `/boot/config.txt`

### Why does shut down and reboot take ages?

Previous to RetroPie 3.4, there was whereby EmulationStation was terminated on reboot/shut down, rather than shutting down 'cleanly'. This has now been fixed, so every time you reboot EmulationStation rewrites all the metadata about your roms so that play counts, last-played dates, etc., are saved. This has the side-effect of the causing the whole process to take longer, relative to how many ROMs you have. MAME/FBA ROMs can often form the bulk of libraries, so it might be helpful to remove clones by [rebuilding your set with a custom parent-only DAT](https://github.com/retropie/retropie-setup/wiki/Managing-ROMs).