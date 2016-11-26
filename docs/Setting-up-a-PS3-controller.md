## Recent Versions of RetroPie (3.0+, 4.0+)

The most recent versions of RetroPie include the packages needed for setting up a PS3 controller. Connecting over USB is Plug-and-Play--literally just plug your controller into the Pi while EmulationStation is running and it should detect a gamepad to configure. Connecting a PS3 controller via Bluetooth requires installation of a special PS3 driver located in RetroPie setup.

## Configuring a PS3 controller to connect via Bluetooth

Before booting the Raspberry Pi, make sure that a supported Bluetooth adapter is connected (for the Pi 3, onboard Bluetooth works perfectly as of RetroPie 4.0+). If you have a Playstation 3 console near by, make sure it is **totally powered off**--either unplugged or switched off in the back--because the PS3 controller may try to automatically pair with the console otherwise.  While a separate powered USB hub is not required to set up a controller, be mindful of your overall power draw when attaching peripherals. If you are overclocking, for example, it will be much safer to use a powered USB hub than drawing current from the Pi itself.

After your Pi boots up, you need to enter RetroPie setup. You can do this one of two ways:

* Setting up your keyboard or PS3 controller as a USB gamepad in EmulationStation (you **must** configure a gamepad before you can use EmulationStation), navigating to the "RetroPie" icon in the Home Screen, and selecting it using whatever key you mapped "A" to on your gamepad. 
* Pressing F4 to quit EmulationStation and running the Retropie script from the terminal. Once you're in the terminal, follow these instructions to run the `retropie_setup.sh` script.

### Using the RetroPie GUI to configure the PS3 Controller Bluetooth Connection

__Note: Do not enable other bluetooth options as these will conflict with the PS3 specific bluetooth setup (sixad)__

1. Navigate to the "RetroPie" icon in the Home Screen and select it using whatever key you mapped "A" to on your gamepad
1. Once in the RetroPie GUI, navigate to the RetroPie Setup Option.
1. A terminal-like window will pop up with a list of choices; navigate to the "Drivers" option and select it.
1. Select PS3 Controller Driver, and then select Install.
1. Once installation completes, exit RetroPie setup and return to the EmulationStation Home Screen.
1. Press "Start" to enter the EmulationStation Menu, and select Configure Input.
1. Disconnect your PS3 controller from USB. Now hold the PS button on the controller down until you see the lights on it flash sequentially. The controller should now be connected via Bluetooth.
1. Emulation Station should now detect another gamepad connected. Hold any button down on the controller to begin configuring it.

And you now have a functional PS3 controller over Bluetooth.

Some PS3 Controller clones (such as the Shanwan PS3 Controllers) will not connect over bluetooth until they are physically connected and removed from a normal USB connection.  If you are having issues pairing a controller, try connecting it via USB for several seconds, disconnecting it, and then pairing it over Bluetooth.

### Using the RetroPie shell to configure the PS3 Controller Bluetooth Connection

__Note: Do not enable other bluetooth options as these will conflict with the PS3 specific bluetooth setup (sixad)__

At the EmulationStation Home Screen, press F4 to quit EmulationStation and run the Retropie script from the terminal. Once you're in the terminal, follow these instructions to run the `retropie_setup.sh` script.

    shell
    sudo RetroPie-Setup/retropie_setup.sh

Although it is not required, it is always a good idea to update the setup script by selecting

    S Update RetroPie-Setup Script

After updating, run the `retropie_setup.sh` script again.

Now select `Manage packages` > `Manage driver packages` > `ps3controller`

After it finishes compiling, the GUI prompt will ask you to make sure that your Bluetooth dongle is connected. Press enter and connect your PS3 controller.

Once this is done, you can disconnect the controller USB cable, and press the Playstation button to pair it via Bluetooth.

After installation of PS3 controller driver bluetooth connection of new controllers will be configured automatically if you connect them over usb. 

### Persisting bluetooth
For bluetooth pairing to persist between reboots you need to make sure sixad is executed during startup.
Exit EmulationStation and and edit `rc.local`.

    shell
    sudo nano /etc/rc.local

Add `sixad --start &` before the line `exit 0` and save (ctrl-x then y)

## Manually setting input
If the keys stop working in-game after switching to bluetooth or you want to configure inputs manually you can do this the recommended way using the RetroArch configuration UI (under `settings` > `input`) or by creating a input map manually:

    cd /opt/retropie/configs/all/retroarch-joypads/
    touch PLAYSTATION\(R\)3\ Controller.cfg
    nano PLAYSTATION\(R\)3\ Controller.cfg

Example config:

    input_driver = "udev"
    input_device = "PLAYSTATION(R)3 Controller"
    input_b_btn = "13"
    input_y_btn = "15"
    input_select_btn = "0"
    input_start_btn = "3"
    input_up_btn = "4"
    input_down_btn = "6"
    input_left_btn = "7"
    input_right_btn = "5"
    input_a_btn = "14"
    input_x_btn = "12"
    input_l_btn = "10"
    input_r_btn = "11"
    input_l2_btn = "8"
    input_r2_btn = "9"
    input_l3_btn = "1"
    input_r3_btn = "2"
    input_l_x_plus_axis = "-0"
    input_l_x_minus_axis = "+0"
    input_l_y_plus_axis = "+1"
    input_l_y_minus_axis = "-1"
    input_r_x_plus_axis = "-2"
    input_r_x_minus_axis = "+2"
    input_r_y_plus_axis = "+3"
    input_r_y_minus_axis = "-3"
    input_enable_hotkey_btn = "0"
    input_exit_emulator_btn = "3"

## For older versions of RetroPie
For setting up the PS3 Controller we're going to be following This [post](http://booting-rpi.blogspot.ro/2012/08/dualshock-3-and-raspberry-pi.html)

(now oddly i couldn't get to Pair constantly with bluetooth but worked over USB, but for those getting it to work over bluetooth's sake we're going to follow the guide step by step)

First: Besides having a bluetooth adapter :P we're going to install all dependencies required

    sudo apt-get install bluetooth blueman bluez-hcidump checkinstall libusb-dev libbluetooth-dev joystick pkg-config

Now that's installed (and a reboot if you plugged in your dongle afterwards) run ```hciconfig``` to make sure it's seeing your dongle, if it has not, a dependency failed to install or your dongle is not supported by RetroPie SD (Raspbian) or the said OS running. you should see an output with information like this:

    pi@raspberrypi ~ $ hciconfig
    hci0: Type: BR/EDR Bus: USB
     BD Address: 00:1F:81:00:06:20 ACL MTU: 1021:4 SCO MTU: 180:1
    UP RUNNING PSCAN
    RX bytes:1260 acl:0 sco:0 events:46 errors:0
    TX bytes:452 acl:0 sco:0 commands:45 errors:0

Next we're going to pair using this [tool](http://www.pabr.org/sixlinux/sixlinux.en.html)
Downloading and compiling is pretty quick and straight forward:

    wget http://www.pabr.org/sixlinux/sixpair.c
    gcc -o sixpair sixpair.c -lusb

however sixpair must be run as root, so connect via USB and run ```sudo ./sixpair```.
If successful you should see: 

    Current Bluetooth master: DE:AD:BE:EF:00:00
    Setting master bd_addr to: 00:1F:81:00:06:20 

now this is where the magic happens

we're going to install an Sixaxis Manager this is what will let us use the controller as an input over bluetooth and USB. (mycase i only got over USB you may vary!)

    wget http://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.1/QtSixA-1.5.1-src.tar.gz
    tar xfvz QtSixA-1.5.1-src.tar.gz

The source code requires a patch to compile correctly as of right now, so we'll download and apply it

    wget https://bugs.launchpad.net/qtsixa/+bug/1036744/+attachment/3260906/+files/compilation_sid.patch
    patch ~/QtSixA-1.5.1/sixad/shared.h < compilation_sid.patch

It should now correctly build and install 

    cd QtSixA-1.5.1/sixad
    make
    sudo mkdir -p /var/lib/sixad/profiles
    sudo checkinstall


now if we want to make it so per every time we need it on demand: we start the controller daemon like so:

    sudo sixad --start (when it displays its searching, press the PS Button and your golden~!)

if we want it at boot time then we use this command:

    sudo update-rc.d sixad defaults
    reboot

if you have any issues with the controller you can debug it with `sudo jstest /dev/input/js0`

#### Disconnect Bluetooth Controller
To disconnect the controller, hold down the ps3 button for 10 seconds.