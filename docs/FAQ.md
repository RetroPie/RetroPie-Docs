- [Why do some emulators not show up?](FAQ#why-do-some-emulators-not-show-up)
- [Why can't I SSH as root anymore?](FAQ#why-cant-i-ssh-as-root-anymore)
- [Reset ownership/permissions of /home/pi/RetroPie roms](FAQ#reset-ownershippermissions-of-homepiretropie-roms)
- [Where did the desktop go?](FAQ#where-did-the-desktop-go)
- [Why does shut down and reboot take ages?](FAQ#why-does-shut-down-and-reboot-take-ages)
- [How do I hide the boot text?](FAQ#how-do-i-hide-the-boot-text)
- [How do I boot to the desktop or Kodi?](FAQ#how-do-i-boot-to-the-desktop-or-kodi)
- [How do I remove the black borders?](FAQ#how-do-i-remove-the-black-borders)
- [How do I change which buttons to press to exit an emulator with a controller?](FAQ#how-do-i-change-which-buttons-to-press-to-exit-an-emulator-with-a-controller)
- [How do I extend the available space when upgrading to a larger SD card?](FAQ#how-do-i-extend-the-available-space-when-upgrading-to-a-larger-sd-card)
- [How would I start from command line, say, the SNES emulator by itself?](FAQ#how-would-i-start-from-command-line-say-the-snes-emulator-by-itself)
- [Is there another way to set up the gamepad for use, e.g., within the snes emulator?](FAQ#is-there-another-way-to-set-up-the-gamepad-for-use-eg-within-the-snes-emulator)
- [The PSX emulator reports no BIOS found. What do I do?](FAQ#the-psx-emulator-reports-no-bios-found-what-do-i-do)
- [How do I calculate the md5sum or CRC32 of a BIOS file?](FAQ#how-do-i-calculate-the-md5sum-or-crc32-of-a-bios-file)
- [Which memory split should I use?](FAQ#which-memory-split-should-i-use)
- [Why aren't my in-game saves working properly?](FAQ#why-arent-my-in-game-saves-working-properly)
- [Why Can't I Insert Coins in Arcade Emulators?](FAQ#why-cant-i-insert-coins-in-arcade-emulators)
- [The `retropie_setup` and `runcommand` menus have very small fonts on my screen, how can I increase the console font size?](FAQ#how-can-i-increase-the-console-font-size)
- [How can I recover my RetroPie after I enabled the experimental OpenGL driver?](FAQ#how-can-i-recover-my-retropie-after-enabling-the-desktop-opengl-driver)
- [How can I disable a USB device without disconnecting it?](FAQ#how-can-i-disable-a-usb-device-without-disconnecting-it)
- [Why Emulationstation doesn't start anymore after an update?](FAQ#why-emulationstation-doesnt-start-automatically-after-an-update)
- [My Xbox controller is not working properly with Moonlight Embedded/PPSSPP](#my-xbox-controller-is-not-working-properly-with-moonlight-embeddedppsspp)


### Why do some emulators not show up?

The RetroPie SD image only ships with the most common emulators, if a system you want is missing you first need to make sure that emulator is installed. The details for installing additional emulators is explained on the [first installation page](First-Installation#installing-additional-emulators--ports)

If the system still doesn't show up in Emulation Station, only emulators with ROMs inside its respective folder will show up in the EmulationStation GUI (given that the specific emulator is installed). For example, for the Nintendo 64 emulator to show up, you must have at least one ROM in the `~/RetroPie/roms/n64/` folder. For ROM types supported by each emulator, go to the wiki page for that specific system/emulator. 

### Why can't I SSH as root anymore?

The `root` account password is disabled by default (as is the case for Raspberry Pi OS and many other Linux distros). To allow remote SSH access using the `root` account:

* Enable `root` login with SSH by editing the SSH configuration file. Run:
    
    `sudo nano /etc/ssh/sshd_config`
    
    The line 

    `#PermitRootLogin without-password`

    should be changed to

    ```PermitRootLogin yes```

    The file can be saved by typing `Ctrl+X` and confirming the changes.

* Set a password for the `root` account. Run:
   
   `sudo passwd root`
   
   and pick a reasonable complex password for the account.


For more details about the `root` account and its usage, see:

* <https://www.raspberrypi.org/documentation/computers/using_linux.html#root-and-sudo>
* <http://elinux.org/R-Pi_Troubleshooting#I_don.27t_know_the_root_password>

### Reset ownership/permissions of /home/pi/RetroPie roms

To reset all your rom file ownerships back to the "pi" user, enter the [RetroPie-Setup Script](Updating-RetroPie)

navigate to **Configuration / Tools >> resetromdirs**

### Where did the desktop go?

The PIXEL (formerly LXDE) desktop environment was removed from the RetroPie image to keep it smaller.

It can easily be installed from the [RetroPie Setup Script](Updating-RetroPie)

in **Configuration / Tools >> Raspbiantools >> Install Pixel Desktop Environment**

after installation it will be accessible from the ports menu of EmulationStation or can be called from the command line with `startx`

![raspbian](https://cloud.githubusercontent.com/assets/10035308/19827420/347e1d6a-9d5e-11e6-8146-d814c8dd087b.png)

You can also install it manually with:

```
sudo apt install --no-install-recommends lxde
sudo apt install xorg raspberrypi-ui-mods rpi-chromium-mods
```

And then you can access it from the terminal by typing in

`startx`

After installation your pi will boot into the desktop environment, you can change the behaviour to boot into emulationstation by selecting the autostart option for emulationstation from the configuration/tools section of the setup script, or you can set the autologin to console option from the boot options of the raspi-config menu.

Note that failing to run startx after the installation may prevent other XWindow-based applications from starting (e.g. Micropolis port), so do launch the desktop after installation to ensure that it is fully set up.

**Note that you cannot run PIXEL and Retropie at the same time. You will need to log out of PIXEL completely to start EmulationStation**

### Why does shut down and reboot take ages?

Previous to RetroPie 3.4, there was an issue whereby EmulationStation was terminated on reboot/shut down, rather than shut down 'cleanly'. This has now been fixed, so every time you reboot/shut down EmulationStation rewrites all metadata about your roms, so that play counts, last-played dates, etc., are saved. This has the side-effect of the causing the whole process to take longer, relative to how many ROMs you have. MAME/FBA ROMs can often form the bulk of libraries, so it might be helpful to remove clones by [rebuilding your set with a custom parent-only DAT](Managing-ROMs).

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

`sudo nano /etc/motd`

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

**Hide Autologin Text: (Raspbian 9 "Stretch" and newer)**

`sudo nano /etc/systemd/system/getty@tty1.service.d/autologin.conf`

change

```
ExecStart=-/sbin/agetty --autologin pi --noclear %I $TERM
```

to

```
ExecStart=-/sbin/agetty --skip-login --noclear --noissue --login-options "-f pi" %I $TERM
```


### How do I boot to the desktop or Kodi?

In retropie setup script>>Configuration / tools>>autostart

![autostart](https://cloud.githubusercontent.com/assets/10035308/15987124/7699dbcc-2fda-11e6-8a1f-902e3177d782.png)

- **Start EmulationStation at Boot:** Boots into EmulationStation.
- **Start Kodi at Boot:** Boots into Kodi- if you exit Kodi you will be returned to EmulationStation.
- **Manually Edit /opt/retropie/configs/all/autostart.sh:** you can manually add other programs to start on boot.
- **Boot to text console (autologin):** Boots into the terminal.
- **Boot to Desktop:** If you have a desktop environment installed like LXDE this will boot into the desktop. Note you'll want to disable the retropie splash from the setup script first.

### How do I remove the black borders?

See [Overscan](Overscan)

### How do I extend the available space when upgrading to a larger SD card?

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
sudo apt install libarchive-zip-perl
```

### Which memory split should I use?

Using the raspi-config or rpi-update script, one can change the RAM splitting for the Raspberry Pi. Depending on your hardware setup you might have to change your splitting.

From [ToadKing](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=112241#p112241):
> If you're on 224/32, you can't run it (i.e., RetroArch) on a HD display. You'll have to use the 192/64 split at least.

A Raspberry Pi B/B+/2 is highly recommended. The GPU should have at least 256MB RAM. If you have a Raspberry Pi A/A+  it is not possible to scrape games and use system themes. 

### Why aren't my in-game saves working properly?

All retroarch emulators use the same method to save to disk. The default behavior is to only write to the save file upon a clean exit back to emulationstation. This is done by default when exiting the game (eg, via the Exit [Hotkey combination](Controller-Configuration#hotkey)). Hence, if a game happens to completely freeze or crash, it's likely that you will lose in-game progress even after saving via the in-game method.

Besides using save states, one optional method you can use to prevent this accidental loss in progress is the autosave_interval setting. This setting can be changed in `/opt/retropie/configs/all/retroarch.cfg` either with the terminal, Configure Retroarch / Launch RetroArch RGUI under `settings->saving`, or Edit RetroPie/RetroArch configurations under `Manually edit Retroarch configurations`. Once autosave_interval is set to equal a number of seconds, retroarch will automatically write to the save file every interval of that number of seconds.

### Why Can't I Insert Coins in Arcade Emulators?

It's whatever is bound to [RetroPad Select](Controller-Configuration).

If there is not a button available to use as Select, [rebind](RetroArch-Configuration#core-input-remapping) to an unused button.

### How can I increase the console font size?

Recent versions of the RetroPie-Setup script include a Console Font script module at **Configuration / tools -> consolefont**. 

Alternatively, you can execute the following command and follow the instructions on screen:

```
sudo dpkg-reconfigure console-setup
```

### How can I recover my RetroPie after enabling the desktop OpenGL driver?
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
  **Note**: If you haven't previously enabled [SSH](SSH) access to the system, then use the instructions to enable SSH on a headless Raspberry Pi OS system from  the [Raspberry Pi site](https://www.raspberrypi.org/documentation/computers/remote-access.html#setting-up-an-ssh-server/):
 > For headless setup, SSH can be enabled by placing a file named ssh, without any extension, onto the boot partition of the SD card from another computer. When the Pi boots, it looks for the ssh file. If it is found, SSH is enabled and the file is deleted. The content of the file does not matter; it could contain text, or nothing at all.
>
> If you have loaded Raspbian onto a blank SD card, you will have two partitions. The first one, which is the smaller one, is the boot partition. Place the file into this one.

### How can I disable a USB device without disconnecting it?

USB devices can be disabled via deauthorization in udev. For example, the following udev rule will disable a Mayflash Wireless Wii U Adapter:

```
SUBSYSTEM=="usb", ATTRS{idVendor}=="0079", ATTRS{idProduct}=="1800", ATTR{authorized}="0"
```
The values for idVendor and idProduct can be determined by the command ```lsusb``` in the Retropie console. Alternatively, the following command(s) will show them for a particular joystick device (js**X**).
```
udevadm info -q all -n /dev/input/js0 | grep 'VENDOR_ID\|MODEL_ID'
```
To disable the device in question, substitute your idVendor and idProduct values in the above udev rule and save it to a file named `/etc/udev/rules.d/60-disabled_devices.rules` (the name between `60-` and `.rules` is arbitrary). That should disable the USB device on the next reboot or after running the command ```sudo udevadm trigger```.

To re-enable the device, just delete the file or change ATTR{authorized}="0" to `1`.

### Why Emulationstation doesn't start automatically after an update ?

Due to a bug in the `systemd` Raspbian package, certain OS upgrades will break the auto-login configuration for the `pi` user, stopping Emulationstation to start automatically. After the update, you're presented with a text mode screen and login prompt (`retropie login:`).

To fix this, login to the system with the `pi` user (default password is `raspberry`), then start the Raspbian configuration utility by running:

```
sudo raspi-config
```

To fix the auto-login configuration, go to **3 Boot Options**, choose **Desktop/CLI** and finally choose the **Console Autologin** option. Go back to the main menu and choose <kbd>Finish</kbd> and Reboot your Pi. 

After the reboot, Emulationstation should start automatically.

### My Xbox controller is not working properly with Moonlight Embedded/PPSSPP

Some applications like [Moonlight Embedded](https://github.com/moonlight-stream/moonlight-embedded) or emulators like [PPSSPP](https://ppsspp.org) expect the Xbox 360/One controllers to have the analog triggers (LT/RT) exposed as axis instead of buttons.

RetroPie's `xpad` Xbox controller driver is configured to map the controller's LT/RT as buttons - insteads of axis - and this option makes the controller not working properly in applications that use SDL gamepad mappings.

To solve the problem, one of the following solutions can be used:

* uninstall the `xpad` driver, by running the RetroPie setup script and going to _Manage packages_ -> _Manage driver packages_. Select the `xpad` entry and then use the _Remove_ option.

* configure the `xpad` driver's to retain the LT/RT original axis behavior. Edit the `/etc/modprobe.d/xpad.conf` file so it contains:

   ````
	 options xpad triggers_to_buttons=0
	 ````

After the modifications above, the controller _needs_ to be [re-configured](Controller-Configuration) again in EmulationStation.
