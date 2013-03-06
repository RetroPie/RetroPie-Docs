For setting up the PS3 Controller we're going to be following This [post](http://booting-rpi.blogspot.ro/2012/08/dualshock-3-and-raspberry-pi.html)

(now oddly i couldn't get to Pair constantly with bluetooth but worked over USB, but for those getting it to work over bluetooth's sake we're going to follow the guide step by step)

First: Besides having a bluetooth adapter :P we're going to install all dependencies required

sudo apt-get install bluez-utils bluez-compat bluez-hcidump checkinstall libusb-dev  libbluetooth-dev joystick

now that's installed (and a reboot if you plugged in your dongle afterwards) run "hciconfig" to make sure it's seeing your dongle, if it has not, a dependency failed to install or your dongle is not supported by RetroPie SD (Raspbian) or the said OS running. you should see an output with information like this:

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

however sixpair must be run as root, so connect via USB and run "sudo ./sixpair"
if successful you should see: 
Current Bluetooth master: DE:AD:BE:EF:00:00
Setting master bd_addr to: 00:1F:81:00:06:20 

now this is where the magic happens

we're going to install an Sixaxis Manager this is what will let us use the controller as an input over bluetooth and USB. (mycase i only got over USB you may vary!)

wget http://sourceforge.net/projects/qtsixa/files/QtSixA%201.5.1/QtSixA-1.5.1-src.tar.gz
tar xfvz QtSixA-1.5.1-src.tar.gz
cd QtSixA-1.5.1/sixad
make
sudo mkdir -p /var/lib/sixad/profiles
sudo checkinstall

now if we want to make it so per every time we need it on demand: we start the controller daemon like so:
 sudo sixad --start (when it displays its searching, press the PS Button and your golden~!)

if we want it at boot time then we use this command:
sudo update-rc.d sixad defaults
reboot

if you have any issues with the controller you can debug it with "sudo jstest / dev/input/js0"

this Guide, we have thanks to Donnerstag over at http://booting-rpi.blogspot.ro/ as well as: http://blog.onsw.net/yuta/  (credit must go where its due :3)