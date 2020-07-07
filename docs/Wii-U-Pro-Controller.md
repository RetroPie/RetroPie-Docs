# About
This how-to will explain the fairly easy setup of a Wii U Pro Controller (or any Wii controller) within a jessie based RetroPie Setup. After the setup the controller will connect automatically when it is turned on and can be disconnected off with the power button on the controller.
The steps are based on the XWiimote description in the ArchWiki: https://wiki.archlinux.org/index.php/XWiimote

# Prerequisites
This will only work on Debian Jessie based distributions. So you either have to get the latest Raspbian version (Debian Jessie based) and use the RetroPie-Setup script or use RetroPie 3.5.

# Steps
1. Either open the commandline on the pi by exiting emulationstation or ssh into it

2. Ensure your bluetooth adapter is setup correctly and working

3. Enter 'sudo bluetoothctl' command

4. The bluetooth control input should open, now type in the following commands in this order (you can use the TAB key to auto complete the mac address for the pair and connect command)
```shell
power on
agent on
pairable on
<press red sync button>                                         # not a command press the button on the controller
scan on
pair <MAC of the found wiimote, use TAB for autocompletion>     # note: we do not explicitly connect, we just pair!
connect <MAC of the wiimote>                                    # there seems to be a pretty short timeout, so execute this immediately after the pairing command
trust <MAC of the wiimote>
disconnect <MAC of the wiimote>
```
Now you're done, press any button on the controller and it should connect, press the power button and it should disconnect, it also persists after a reboot

# Lights
There is a github project you can easily install that will light up the appropriate lights on your controllers based upon their order on your system.  It's just a matter of running 2 commands on your pi.  The project is found here: https://github.com/pyhammond/retropie_wiimote_lights