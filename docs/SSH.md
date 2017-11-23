SSH stands for secure shell. You can remotely connect to the raspberry pi terminal with an SSH client. A popular ssh client is [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) for Windows. The ssh command can be used on macOS and GNU/Linux

**NOTE** Your Raspberry Pi needs to be connected to the same network (either via Ethernet or Wifi Dongle) as the computer you are accessing it from. 

## Enable SSH

**Note:** Starting with RetroPie 4.2, in order to keep the default image secure, SSH is disabled by default. It can be enabled in either of the two ways listed below.

1) Pre-boot. From a system with an SD-card reader, access the /boot/ directory and create an empty file called ssh

2) In **raspi-config**: after booting.
```
sudo raspi-config
```
**interfacing options >> SSH >> Enable >> reboot your pi**

For more information on why SSH was disabled see [HERE](https://www.raspberrypi.org/blog/a-security-update-for-raspbian-pixel/)

### When using BerryBoot

When using RetroPie with [BerryBoot](http://www.berryterminal.com/doku.php/berryboot) you cannot use `raspi-config`. There is a workaround to enable SSH:
* Boot to RetroPie (via BerryBoot)
* Enter shell by pressing Ctrl + F4
* `cd /boot`
* `sudo touch ssh`
* `sudo reboot now`
* Done!

## Connecting

When you first start putty you can sign in with the following credentials:

![putty](https://cloud.githubusercontent.com/assets/10035308/10655671/23eaa6b2-7834-11e5-8c85-9266c5ab808a.png)

You can also use your raspberry pi's ip address instead of `retropie`

### Default Login:

username: **pi**

password: **raspberry**

See [here](FAQ#why-cant-i-ssh-as-root-anymore) if you wish to log in as root.

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
**list Files in Current Directory**
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
