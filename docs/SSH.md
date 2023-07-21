Enabling SSH (Secure Shell) allows remote connection to the Raspberry Pi. This provides a means for adding roms, changing configuration, updates, and other convenient procedures by using SSH and SFTP clients to connect to the Raspberry Pi. For this instruction and for the sake of simplicity, this guide assumes that both the Raspberry Pi and the computer you are using to remotely connect to it are on the same local network.

**NOTE: Your Raspberry Pi needs to be connected to the same network/router (either via Ethernet or Wifi Dongle) as the computer you are accessing it from.**

Here are a few (free) popular clients to try. These need to be installed on the PC, Mac, or other computer you are using to connect *to* the Raspberry Pi:

* Windows:
  * [Windows 10 SSH Client](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=gui) - Available since Windows 1809 build.
  * [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) - Very simplistic access to allow for console commands, but does not feature the ease of drag & drop for ROMs and other files.
  * [WinSCP](https://winscp.net/eng/download.php) - An SFTP client that features an easy way to drag & drop files. Console commands are also possible (and even integrates with Putty) but is a secondary user interface found in the `Commands` > `Open Terminal` or `Commands` > `Open in Putty` menus.
  * [MobaXterm](https://mobaxterm.mobatek.net/) - A feature-rich console commands and drag & drop client that includes most ways to remotely connect to another computer, including SSH, SFTP, and even VNC (allows viewing the screen of another computer).
* Mac:
  * [CyberDuck](https://cyberduck.io/?l=en)


## Enable SSH

**Note**: Starting with RetroPie 4.2, in order to keep the default image secure, [SSH is disabled by default](https://www.raspberrypi.org/blog/a-security-update-for-raspbian-pixel/). You will not be able to remotely connect to it until it has been enabled using `ONE` of the instructions below.

### (Option 1) From the SD Card

If your computer has an SD-card reader or a special USB stick that allows inserting an SD card, plug it into your computer, open the new drive to access your SD-card's `boot` partition,  and create an empty file called `ssh` or `ssh.txt` in the root directory. Ignore any warnings about the drive needing to be repaired (on Windows).

### (Option 2) From the RetroPie menu

1. Select `raspi-config` from the RetroPie menu after booting up.
2. Select `Interface Options`
3. Select `SSH`
4. Choose `Yes`
5. Select `Ok`
6. Choose `Finish`

### (Option 3) When using BerryBoot

When using RetroPie with [BerryBoot](http://www.berryterminal.com/doku.php/berryboot) you cannot use `raspi-config`. There is a workaround to enable SSH:

1. Boot to RetroPie (via BerryBoot)
2. Enter shell by pressing <kbd>Ctrl + F4</kbd>
3. `cd /boot`
4. `sudo touch ssh`
5. `sudo reboot now`
6. Done!

## Connecting

Four credentials are needed to remotely connect to your Raspberry Pi: IP address, port, username, and password. These will be the same with any client (WinSCP, Putty, MobaXterm, etc).

### Default Login
In your chosen client, enter the following:

* IP address: **See below note**
* Port: `22`
* Username: `pi`
* Password: `raspberry`

**Note: The IP address is unique to your local network, and can be found by selecting the `Show IP` option in the `RetroPie` menu after booting up your Raspberry Pi.**

Example using Putty:

![putty](https://cloud.githubusercontent.com/assets/10035308/10655671/23eaa6b2-7834-11e5-8c85-9266c5ab808a.png)

Example using WinSCP:

![winscp](https://user-images.githubusercontent.com/540857/106331841-9f56b700-6253-11eb-8735-7e92b00375c5.png)

### Root Access

**Warning! Root access is meant for advanced users only, and only for functions not possible with the `pi` user. Do not use `root` when transferring ROMs or other tasks available to the default `pi` user.**

For more advanced users, root access can more easily allow for editing protected files such as the `config.txt` when [overclocking](Overclocking). This allows users to remotely make changes, reboot, and instantly view performance changes.

[See here if you wish to log in as root](FAQ#why-cant-i-ssh-as-root-anymore).

## Common Terminal Commands:

**Reboot:**
```
sudo reboot
```
**Shutdown:**
```
sudo shutdown -h now
```
**Change Directory**
```
cd /path/to/directory
```
**List Files in Current Directory**
```
ls
```
**Retropie Setup Script:**
```
sudo /home/pi/RetroPie-Setup/retropie_setup.sh
```
**Edit Files with Nano:**
```
sudo nano /path/to/file.txt
```
**Change owner to Pi:**
```
sudo chown pi:pi filetobechanged
```
**Change owner of folder and all files in folder to Pi:**
```
sudo chown -R pi:pi /folder/to/be/changed
```

**Make shell script executable:**
```
sudo chmod +x yourshellscript.sh
```

## Extra Configurations

If you find that you are getting weird characters on the dialog gui for the RetroPie Setup script you can change the font encoding to make it look pretty again.

![font encoding](https://cloud.githubusercontent.com/assets/10035308/14335542/4353385c-fc19-11e5-98a3-abc555191190.PNG)
![font encodingfinal](https://cloud.githubusercontent.com/assets/10035308/14335541/43404ed6-fc19-11e5-8b7c-12c9321edb4b.PNG)
