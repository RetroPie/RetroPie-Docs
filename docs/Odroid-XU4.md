# Odroid XU4

This is a guide on how to build RetroPie on the Odroid XU4. This is assuming you are starting with a prebuilt image of Ubuntu from HardKernel's Website:

## Download Ubuntu Minimal Image for Odroid XU3/XU4:

https://odroid.in/ubuntu_16.04lts/

Direct Link [Here](https://odroid.in/ubuntu_16.04lts/ubuntu-16.04-minimal-odroid-xu3-20160706.img.xz)

Extract the .xz file with a program like [7zip](http://www.7-zip.org/download.html)

Write the .img file to your SD card or EMMC module with something like [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/)

Unlike the RetroPie SD Image, the Odroid image will autoexpand the filesystem so there is no need for that step here.

## Install RetroPie:

Preliminary steps:

1. As the fresh install of Ubuntu includes only the root user (password: odroid) a new user has to be created:

```
adduser NameOfYourChoice
```
2. Add new created user to the sudo group:
```
usermod -a -G sudo NameOfYourChoice
```
3. Upgrade system including the kernel:
```
sudo apt update
sudo apt upgrade
sudo apt dist-upgrade
sudo apt install linux-image-xu3
shutdown -r now
```
4. Adjust your time and timezone:
```
sudo dpkg-reconfigure tzdata
```
5. Install the odroid-utility in order to resize the root partition:
```
sudo apt-get install unzip
wget https://github.com/mdrjr/odroid-utility/archive/master.zip
unzip master.zip
./odroid-utility-master/odroid-utility.sh
```
6. Set the locale settings. Below you can find example settings:
```    
apt-get install language-pack-en-base
update-locale LC_ALL="en_US.UTF-8"
update-locale LANG="en_US.UTF-8"
update-locale LANGUAGE="en_US.UTF-8"
dpkg-reconfigure locales
```

sudo apt-get install -y git
Installing the RetroPie Setup Script:
```
cd
git clone --depth=1 https://github.com/RetroPie/RetroPie-Setup.git
```

Run the Setup Script:

```
cd RetroPie-Setup
sudo ./retropie_setup.sh
```

**Note** if you have issues while compiling modules and it freezes up on you, then you need to tell it to only compile with one core by running the setup script with this:

```
sudo MAKEFLAGS="-j1" ./retropie_setup.sh

```

## Installing Modules

All modules can be installed from the RetroPie Setup Script. First and foremost the two main packages you need in order for the majority of your system to run are RetroArch and EmulationStation:

#### Installing EmulationStation:

- Option 5: Install EmulationStation

Killing X `sudo service lightdm stop`

open new terminal `ctrl+alt+F1`

#### Install EmulationStation Theme

- Option 3: Install Themes

#### Installing RetroArch:

- Option 5: Install RetroArch

## Installing Emulators:

- Option 5: Choose your emulators

## Advanced Configuration

#### AutoStart EmulationStation

- Option 3: Autostart EmulationStation 

#### Rom Transfer

- Option 3: Enable USBRomService

#### Samba Shares

- Option 3: Enable Samba Shares

### Ubuntu 14

#### Boot to Console:

```
sudo -s

sudo echo "manual" >> /etc/init/lightdm.override

```

To start lightdm on command:

```
sudo start lightdm
```

To restore your system so that lightdm is always started on boot:

```
sudo rm /etc/init/lightdm.override
```

#### Disable Screen Blanking in Console:

```
sudo nano /etc/kbd/config
```
comment out

```
BLANK_TIME
POWERDOWN_TIME
```

#### Fix sound not working/stuttering

If you have troubles with no sound or sound stuttering badly in menu or game, check your CPU usage via top or htop. If pulseaudio is using more than 20% then it may be the culprit. In my case, it was using 80%! I had only one sound card output (hdmi) so I completely removed pulseaudio with:

```
sudo apt-get --purge remove pulseaudio
```

### Ubuntu 16 (systemd)

#### Boot to Console:

    sudo systemctl disable lightdm

To start lightdm on command:

    sudo systemctl start lightdm

To restore your system so that lightdm is always started on boot:
    
    sudo systemctl enable lightdm

#### Auto-login on startup
 
Update visudo editor:

	sudo update-alternatives --config editor

Run visudo:

	sudo visudo

This will open up /etc/sudoers file in editor you configured in first step. Add the following line to the end of the file:

	odroid ALL=(ALL) NOPASSWD:ALL

This tells sudo that the odroid user doesn't need a password. Save and quit.

Then remove your password:

	sudo passwd -d odroid

Test it all worked:

        sudo date

Should give you the date without asking for a password.

Edit the startup of our tty1 (replace with any tty of choice):

	sudo systemctl edit getty@tty1

Add the following text, save and exit

	[Service]
	ExecStart=
	ExecStart=-/sbin/agetty -a odroid --noclear %I $TERM

Finally, restart the whole mess:

        sudo systemctl restart getty@tty1

#### Disable Screen Blanking in Console:

Edit /media/boot/boot.ini with your editor of choice.

Search for:

    no_console_suspend 

and replace it with:

    no_console_suspend consoleblank=0

Finally, run:

    bootini

and reboot for good luck:

    sudo reboot

#### Fix sound not working/stuttering

If you have troubles with no sound or sound stuttering badly in menu or game, try disabling pulseaudio:

    mkdir ~/.pulse
    echo "autospawn=no" >> ~/.pulse/client.conf
    pulseaudio -k

Then reboot, or restart emulationstation.

If the audio still isn't great, stutters or pops or echos, try the following:

Go to: `RetroPie -> RetroArch -> Settings -> Audio`

And set: `Audio Latency (ms) = 192`

Then don't forget to save! `Configurations -> Save Current Configuration`

Feel free to play with the value until it sounds right for you.

#### Fix games running too quickly or inconsistently

Go to: `RetroPie -> RetroArch -> Settings -> Frame Throttle`

And set: `Maximum Run Speed = 1.0x`

Then don't forget to save! `Configurations -> Save Current Configuration`
