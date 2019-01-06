- [Why do some emulators not show up?](FAQ#why-do-some-emulators-not-show-up)
- [Why can't I SSH as root anymore?](FAQ#why-cant-i-ssh-as-root-anymore)
- [Reset ownership/permissions of /home/pi/RetroPie roms](FAQ#reset-ownershippermissions-of-homepiretropie-roms)
- [Where did the desktop go?](FAQ#where-did-the-desktop-go)
- [Why does shut down and reboot take ages?](FAQ#why-does-shut-down-and-reboot-take-ages)
- [How do I hide the boot text?](FAQ#how-do-i-hide-the-boot-text)
- [How do I boot to the desktop or Kodi](FAQ/#how-do-i-boot-to-the-desktop-or-kodi)
- [How do I remove the black borders](FAQ/#how-do-i-remove-the-black-borders)
- [How do I change which buttons to press to exit an emulator with a controller?](FAQ#how-do-i-change-which-buttons-to-press-to-exit-an-emulator-with-a-controller)
- [Does Super Mario All Stars work?](FAQ#does-super-mario-all-stars-work)
- [How do I extend the available space when upgrading to a larger SD card](FAQ#how-do-i-extend-the-available-space-when-upgrading-to-a-larger-sd-card)
- [How would I start from command line, say, the SNES emulator by itself?](FAQ#how-would-i-start-from-command-line-say-the-snes-emulator-by-itself)
- [Is there another way to set up the gamepad for use, e.g., within the snes emulator?](FAQ#is-there-another-way-to-set-up-the-gamepad-for-use-eg-within-the-snes-emulator)
- [The PSX emulator reports no BIOS found. What do I do?](FAQ#the-psx-emulator-reports-no-bios-found-what-do-i-do)
- [How do I calculate the md5sum or CRC32 of a BIOS file?](FAQ#how-do-i-calculate-the-md5sum-or-crc32-of-a-bios-file)
- [Which memory split should I use?](FAQ#which-memory-split-should-i-use)
- [Why aren't my in-game saves working properly?](FAQ#why-arent-my-in-game-saves-working-properly)
- [Why Can't I Insert Coins in Arcade Emulators?](FAQ#why-cant-i-insert-coins-in-arcade-emulators)
- [The `retropie_setup` and `runcommand` menus have very small fonts on my screen, how can I increase the console font size?](FAQ#how-can-i-increase-the-console-font-size)
- [How can I recover my RetroPie after I enabled the experimental OpenGL driver ?](FAQ#how-can-i-recover-my-retropie-after-enabling-the-desktop-opengl-driver-)
- [How can I recover my RetroPie after I enabled the experimental OpenGL driver ?](FAQ#how-can-I-disable-a-USB-device-without-disconnecting-it-)

### Why do some emulators not show up?

The RetroPie SD image only ships with the most common emulators, if a system you want is missing you first need to make sure that emulator is installed. The details for installing additional emulators is explained on the [first installation page](First-Installation#installing-additional-emulators--ports)

If the system still doesn't show up in Emulation Station, only emulators with ROMs inside its respective folder will show up in the EmulationStation GUI (given that the specific emulator is installed). For example, for the Nintendo 64 emulator to show up, you must have at least one ROM in the `~/RetroPie/roms/n64/` folder. For ROM types supported by each emulator, go to the wiki page for that specific system/emulator. 

### Why can't I SSH as root anymore?

The root password is disabled by default (as is the case for Raspbian and many other linux distros). 

before setting a root password, the following must be edited

```sudo nano /etc/ssh/sshd_config```

look for 

```#PermitRootLogin without-password```

change it to

```PermitRootLogin yes```

then ctrl+x to save, 

next set your root password:

```
sudo passwd root
 
```

restart your Pi to register your changes

see these posts for more details:

https://www.raspberrypi.org/documentation/linux/usage/root.md

http://elinux.org/R-Pi_Troubleshooting#I_don.27t_know_the_root_password

### Reset ownership/permissions of /home/pi/RetroPie roms

To reset all your rom file ownerships back to the "pi" user, enter the [RetroPie-Setup Script](https://github.com/retropie/retropie-setup/wiki/Updating-RetroPie)

navigate to **Configuration / Tools >> resetromdirs**

### Where did the desktop go?

The PIXEL (formerly LXDE) desktop environment was removed from the RetroPie image to keep it smaller.

It can easily be installed from the [RetroPie Setup Script](Updating-RetroPie)

in **Configuration / Tools >> Raspbiantools >> Install Pixel Desktop Environment**

after installation it will be accessible from the ports menu of EmulationStation or can be called from the command line with `startx`

![raspbian](https://cloud.githubusercontent.com/assets/10035308/19827420/347e1d6a-9d5e-11e6-8146-d814c8dd087b.png)

You can also install it manually with:

```
sudo apt-get install --no-install-recommends lxde
sudo apt-get install xorg raspberrypi-ui-mods rpi-chromium-mods
```

And then you can access it from the terminal by typing in

`startx`

After installation your pi will boot into the desktop environment, you can change the behaviour to boot into emulationstation by selecting the autostart option for emulationstation from the configuration/tools section of the setup script, or you can set the autologin to console option from the boot options of the raspi-config menu.

Note that failing to run startx after the installation may prevent other XWindow-based applications from starting (e.g. Micropolis port), so do launch the desktop after installation to ensure that it is fully set up.

**Note that you cannot run PIXEL and Retropie at the same time. You will need to log out of PIXEL completely to start EmulationStation**

### Why does shut down and reboot take ages?

Previous to RetroPie 3.4, there was an issue whereby EmulationStation was terminated on reboot/shut down, rather than shut down 'cleanly'. This has now been fixed, so every time you reboot/shut down EmulationStation rewrites all metadata about your roms, so that play counts, last-played dates, etc., are saved. This has the side-effect of the causing the whole process to take longer, relative to how many ROMs you have. MAME/FBA ROMs can often form the bulk of libraries, so it might be helpful to remove clones by [rebuilding your set with a custom parent-only DAT](https://github.com/retropie/retropie-setup/wiki/Managing-ROMs).

An option has been added starting with RetroPie 3.7 to decide whether or not you want metadata saved on exit.
![main menu](https://cloud.githubusercontent.com/assets/10035308/14507387/a7ee93b8-017f-11e6-94f2-af5a2e158079.png)
![metadata](https://cloud.githubusercontent.com/assets/10035308/14507388/a7fc1bfa-017f-11e6-8f01-8cfed5344542.png)

- **Save Metadata On Exit:** If on, it will read and write all the info for your roms which can lead to long boot and shutdown times if you have large romsets. If you turn it off it will not write those changes which means it also will not write how many times you've played a game, any new game scrapes, etc. This is on by default.

- **Parse Gamelists Only:** If on, it will only read the roms you have scraped, so if you add any new roms it will not look for them unless you turn this back off. it is off by default.

### How do I hide the boot text?

**NOTE that you should be comfortable with editing files in Linux as any wrong edits on the following file can break your boot sequence requiring a reimage of your SD card!**

There are many parts that contribute to the boot text. The boot text is a valuable tool for debugging but if you know you aren't going to be debugging and just want a polished system this outlines some steps that can be taken to make a cleaner boot.

**/boot/cmdline.txt**

A quick summary of the options:

- **logo.nologo**: turns off raspberry(s) at boot
- **quiet**: hide messages
- **console=tty3**: hide more messages (redirect boot messages to the third console)
- **loglevel=3**: hide even more messages (disable non-critical kernel log messages) (Included with default RetroPie image)
- **vt.global_cursor_default=0**: hide blinking cursor
- **plymouth.enable=0**: disable plymouth boot text (Included with default RetroPie Image)

If using a plymouth bootsplash:

- **plymouth.ignore-serial-consoles**: ignore serial consoles
- **plymouth.enable=0**: remove to enable plymouth boot text
- **splash**: enable plymouth splash

You can add the any of the options to the end of the cmdline.txt file **make sure it is all on the same line or else it will break your boot sequence!!!** 

**/boot/config.txt**

- **disable_splash=1**: Disable [large rainbow screen](https://lifehacker.com/what-the-raspberry-pis-rainbow-boot-screen-and-rainbow-1768470271) on initial boot
- **avoid_warnings=1**: will disable warnings such as undervoltage/overheating and isn't really recommended.

Autologin Text:

**Hide login text:**

`touch ~/.hushlogin`

**Hide/modify message of the day** (superseded by .hushlogin if used): 

`nano /etc/motd`

**Hide Autologin Text:**

`sudo nano /etc/systemd/system/autologin@.service`

change

```
ExecStart=-/sbin/agetty --autologin pi --noclear %I $TERM
```

to

```
ExecStart=-/sbin/agetty --skip-login --noclear --noissue --login-options "-f pi" %I $TERM
```

### How do I boot to the desktop or Kodi

In retropie setup script>>Configuration / tools>>autostart

![autostart](https://cloud.githubusercontent.com/assets/10035308/15987124/7699dbcc-2fda-11e6-8a1f-902e3177d782.png)

- **Start EmulationStation at Boot:** Boots into EmulationStation.
- **Start Kodi at Boot:** Boots into Kodi- if you exit Kodi you will be returned to EmulationStation.
- **Manually Edit /opt/retropie/configs/all/autostart.sh:** you can manually add other programs to start on boot.
- **Boot to text console (autologin):** Boots into the terminal.
- **Boot to Desktop:** If you have a desktop environment installed like LXDE this will boot into the desktop. Note you'll want to disable the retropie splash from the setup script first.

### How do I remove the black borders?

See [Overscan](Overscan)

### How do I change which buttons to press to exit an emulator with a controller?

Hotkeys are combinations of buttons you can press in order to access options such as saving, loading, and exiting games. The following defaults are set automatically the first time you set up your controller from emulationstation.

#### Default joypad hotkeys:

Hotkeys | Action | Code Example
:---: | :---: | :---: 
Select | Hotkey | input_enable_hotkey = "6"
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

You can hardcode it globally for all systems here:

```
/opt/retropie/configs/all/retroarch.cfg 
```

or set it by system

```
/opt/retropie/configs/SYSTEMNAME/retroarch.cfg
```

See [HERE](RetroArch-Configuration) for more information on custom controller configs

### Does Super Mario All Stars work?

The ROM does work with lr-snes9x2002 and lr-snes9x2010.

From http://blog.petrockblock.com/2012/07/22/retropie-setup-an-initialization-script-for-retroarch-on-the-raspberry-pi/#comment-818063235:

> I found out that after the selection of a game, the control goes over to the second controller! This seems to be somehow a speciality of the All-Stars ROM. But at least, it is playable :-)

Alternatively, if you only have one controller (or play alone) you can do the following:

From http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=79083

> I managed to figure out a fix so the controls work in Super Mario All-Stars and also doesn't break other games (Mario Kart, Super Bomberman etc). This problem has been bugging me for ages and I had to figure out a way to play this game for nostalgia sake. This fix will unfortunately mean player two controls wont work for other games (but I play alone anyway and this is for people with one controller). Simply post this in your blank retroarch.cfg in the snes folder. P.S Remember to change the button numbers/axis for you own controller.

### How do I extend the available space when upgrading to a larger SD card

1. Navigate to the command line interface by either hitting F4 in EmulationStation or using the main menu to exit
1. Type in the following command: `sudo raspi-config`
1. Select option "7. Advanced Options"
1. Select option "A1. Expand Filesystem"
1. Reboot your Raspberry Pi

### How would I start from command line, say, the SNES emulator by itself?

First you need to make sure your emulators and systems are configured and working properly from EmulationStation.

To **manually start** a specific system and a game from the command line, use `runcommand` as shown below, replacing `<SYSTEM>` with the system you want (nes, snes, gba, arcade, ...) and `<ROM>` with the full path to the ROM to launch (example: `$HOME/RetroPie/roms/snes/My Rom.smc`). Do not forget to keep the surrounding quotes `"`.

    /opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ "<SYSTEM>" "<ROM>"

To **automatically start** a specific system and a game directly instead of EmulationStation, you need to edit `/opt/retropie/configs/all/autostart.sh` and add the above line (again replacing the variables with your own values).
Then, in the same file, remove any line containing `#auto` entirely to avoid EmulationStation or KODI to autostart again.

### Is there another way to set up the gamepad for use, e.g., within the snes emulator?

Follow the [RetroArch-Configuration guide:](RetroArch-Configuration)

### The PSX emulator reports no BIOS found. What do I do?

Ensure the bios file(s) is/are all lowercase and put them in
```shell
/home/pi/RetroPie/BIOS
```

More information about PSX BIOS files can be found on the [PSX page](Playstation-1).

### How do I calculate the md5sum or CRC32 of a BIOS file?

An example to calculate the **md5sum** for the Game Boy Advance BIOS file `gba_bios.bin`
```
md5sum /home/pi/RetroPie/BIOS/gba_bios.bin
```
And this would be how to calculate the **CRC32** for `gba_bios.bin`
```
crc32 /home/pi/RetroPie/BIOS/gba_bios.bin
```

If these commands are not found, then you will need to install **md5sum** and **CRC32**
```
sudo apt-get install libarchive-zip-perl
```

### Which memory split should I use?

Using the raspi-config or rpi-update script, one can change the RAM splitting for the Raspberry Pi. Depending on your hardware setup you might have to change your splitting.

From [ToadKing](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=112241#p112241):
> If you're on 224/32, you can't run it (i.e., RetroArch) on a HD display. You'll have to use the 192/64 split at least.

A Raspberry Pi B/B+/2 is highly recommended. The GPU should have at least 256MB RAM. If you have a Raspberry Pi A/A+  it is not possible to scrape games and use system themes. 

### Why aren't my in-game saves working properly?

All retroarch emulators use the same method to save to your .srm or SRAM. The default behavior is to only write to your srm file upon a clean exit back to emulationstation. This is done by default with the exit hotkey start+select. If the game happens to completely freeze or crash, it's likely that you will lose in-game progress even after saving.

Besides using save states, one optional method you can use to prevent this accidental loss in progress is the autosave_interval setting. This setting can be changed in `/opt/retropie/configs/all/retroarch.cfg`
either with the terminal, Configure Retroarch / Launch RetroArch RGUI under `settings->saving`, or Edit RetroPie/RetroArch configurations under `Manually edit Retroarch configurations`. Once autosave_interval is set to equal a number of seconds, retroarch will automatically write your save data to the srm file every interval of that number of seconds.

### Why Can't I Insert Coins in Arcade Emulators?

It's the Select button in RetroArch. By default, it's right shift. Note that this issue should now be fixed.

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

### How can I increase the console font size?

Recent versions of the RetroPie-Setup script include a Console Font script module at **Configuration / tools -> consolefont**. 

Alternatively, you can execute the following command and follow the instructions on screen:

```
sudo dpkg-reconfigure console-setup
```

### How can I recover my RetroPie after enabling the desktop OpenGL driver ?
Note: this entry applies to the Raspbian Jessie based RetroPie installations.

The OpenGL driver for the Raspberry PI VideoCore GPU was introduced to provide hardware accelerated OpenGL for the X11 OpenGL applications, during the Raspbian Jessie version. From the [original release](https://www.raspberrypi.org/blog/another-new-raspbian-release/):

> [...] In this release we are shipping an experimental OpenGL driver for the desktop which uses the GPU to provide hardware acceleration

>[...]. 
If you don’t use this option, the desktop does have OpenGL support, but it uses a very slow software renderer, which makes all but the most basic OpenGL applications pretty much unusable. The hardware-accelerated version is much faster, and makes some quite decent OpenGL games playable on the Pi.

RetroPie - and the underlying components - are not using the X11 server for display, enabling the OpenGL driver will not add any features or benefits for the system. It also disables with the VideoCore kernel driver used by RetroPie, having the unpleasant side effect of locking the interface and making any direct access to your RetroPie system impossible.
  
To recover from such a situation, there are 2 options:

* Get the SD card out from the Raspberry PI and insert it into a Windows/Linux system. You'll have access to the `boot` partition, where you can find the `config.txt` file used to enable the OpenGL driver. Edit this file and comment/remove the line containing

        dtoverlay=vc4-fkms-v3d           
Insert the SD card back into your RetroPie system and start the system, without the OpenGL driver enabled.
 
 * Access your system via [SSH](SSH) and run `raspi-config` again to disable the OpenGL driver, then reboot the RetroPie system.  
  **Note**: If you haven't previously enabled [SSH](SSH) access to the system, then use the instructions to enable SSH on a headless Raspbian system from  the [Raspbian site](https://www.raspberrypi.org/documentation/remote-access/ssh/):
 > For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. The content of the file does not matter; it could contain text, or nothing at all.
>
> If you have loaded Raspbian onto a blank SD card, you will have two partitions. The first one, which is the smaller one, is the boot partition. Place the file into this one.

**How can I disable a USB device without disconnecting it?**

USB devices can be disabled via usb authorisation in udev. For example, this udev rule will disable a Mayflash Wireless Wii U Adapter:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0079", ATTRS{idProduct}=="1800", ATTR{authorized}="0"
```
The values for idVendor and idProduct can be determined by the command ```lsusb``` in the Retropie console. Alternatively, the following command(s) will show them for a particular joystick device (js…).
```
udevadm info -q all -n /dev/input/js0 | grep 'VENDOR_ID\|MODEL_ID'
```
To disable the device in question, put your vendor and model ids as idVendor and idProduct values in the above udev rule and save it in the text file `/etc/udev/rules.d/60-disabled_devices.rules` (the name between `60-` and `.rules` is arbitrary). That should disable the usb device on the next reboot or after running the command ```sudo udevadm trigger```.

To re-enable the device, just delete the file or change the value "autorized" to `1`.
