###This wiki is how I was able to get my ps4 controller to work with my Raspberry Pi 3. I am using a Bluetooth dongle due to the freezing issues caused by the on-board Bluetooth.

First I disabled the on-board Bluetooth. 

    sudo nano /boot/config.txt

Paste this at the bottom of the config file.

    #Disables On-Board Bluetooth
    dtoverlay=pi3-disable-bt

_If you don't need to update you should still reboot after updating the config.txt_

This is what I do with a fresh install. 

    sudo apt-get update 

    sudo apt-get upgrade

_The upgrade will take some time. I like to reboot after I've upgraded._

    sudo reboot

    sudo apt-get install python3-dev python3-pip

    sudo pip3 install ds4drv

##Now we need to allow a normal user to create a new joystick

    wget https://raw.githubusercontent.com/chrippa/ds4drv/master/udev/50-ds4drv.rules

    sudo mv 50-ds4drv.rules /etc/udev/rules.d/

    sudo udevadm control --reload-rules

    sudo udevadm trigger

##Now Let's Test

    ds4drv --hidraw --led 000008

_Alternitevely you can just do 'ds4drv --hidraw'. I added '--led 000008' for a less bright led on the controller._


You will need to put the PS4 controller into pairing mode. You can do this by holding down the SHARE button & the PS button at the same time. It will starting flickering. It takes mine about 5 seconds to connect.

Once your controller connects go ahead and exit. CNTL + C to stop the test..

##Now we need to make sure ds4drv boots with the Pi

    sudo nano /etc/rc.local
    
And just after “# By default this script does nothing.” we add:

    /usr/local/bin/ds4drv --hidraw --led 000008 &

_Again you can leave out the '--led 000008' if you want the brighter blue lit up on the controllers LED_

It will look like:

    # By default this script does nothing.
    /usr/local/bin/ds4drv --hidraw --led 000008 &
    exit 0

##Now Reboot Your Pi3

Make sure the controller is off. Once the Pi3 completely boots up and shows the window that says no controllers are detected go ahead put the PS4 into pairing mode again by holding down the SHARE button & the PS button. You will have to setup the controller the 1st time you get to the first menu(Just Once). You can turn the controller off by holding down the PS button for about 10 seconds. You can then turn it back on any time you want.

##Hope This Helps

It took me about a week to find the scattered bits and pieces of this wiki. Hopefully this helps! Please add to if you find a better/easier way.
