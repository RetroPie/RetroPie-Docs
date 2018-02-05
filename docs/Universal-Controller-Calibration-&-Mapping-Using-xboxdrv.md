This guide will attempt to detail several advanced controller mappings and calibration techniques suitable for just about any controller. The focus will be on the use of xboxdrv, as it is an extremely versatile tool that can handle almost any situation and is able to be installed directly from from the 'RetroPie Setup' menu. A complete list of its capabilities can be found [here](http://manpages.ubuntu.com/manpages/precise/man1/xboxdrv.1.html). What follows is a grouping of use case scenarios that would be of direct interest to RetroPie Users. New scenarios will be added from time to time. Some of these scenarios will include:

- Keyboard mapping for emulators that don't support controllers natively
- Mouse mapping to analog joysticks for full control of certain arcade and computer games, as well as most Atari system emulators
- Mapping analog triggers as buttons for a faster response time (Commonly seen in the competitive Smash Bros community pre-WiiU)
- Four-way directional input restriction for games like Pac-Man that suffer when diagonal control input is introduced
- Correcting the inner and outer deadzones of analog sticks for finer control and to prevent drifting problems in overly-sensitive or well-worn controllers.
- Configuring a toggle or utilizing unused buttons for auto-fire in any game or emulator
- Correcting unruly analog trigger behavior found in some controllers

`------------------------------------------------------------------------------`

# **(1) Mapping any controller to be read as a standard XBox360 controller.**

None of what is to follow can be accomplished without this first step. The sheer multitude of existing controllers and their loose implementation of "standards" presents a problem to computer software that has a limited definition of what to expect from controller input. Simply mapping a troublesome controller to be read as a standardized XBox360 controller can solve many communication problems without any additional tweaking. However, this same process can also be used to fine-tune a controller in much the same way that you might normally only find in Windows-based solutions. 

First, we need to make sure xboxdrv is installed. This can be done from the 'RetroPie Setup' listing in the 'RetroPie' menu of Emulation Station. Navigate from 'Configuration / Tools' to 'xboxdrv - XBox / XBox360 gamepad driver'. From here, select 'Enable xboxdrv' and wait for it to finish. Once installed and enabled, a configuration will be added to `/etc/rc.local`. Since we will be adding our own custom configuration there later, this command should be removed by selecting 'Disable xboxdrv' from the same menu we enabled it from. With xboxdrv now installed, we now need to discover the core-level device input codes for each button and axis on the physical controller, so that we may then map them to the virtual XBox360 controller. To do this, drop down to the command line by pressing 'F4' on your keyboard, then type:
```
cat /proc/bus/input/devices
```
Press 'Enter' and look for the controller in the list of devices. It can be identified by it's name in the device groupings next to the line beginning with `N: Name=`. Once you find it, make a note of it's event number next to the line beginning with `H: Handlers= `. Next, we'll also need to make note of the event location by name for later use. To do that that, type:
```
ls /dev/input/by-id/
```
Press 'Enter' and your device should be listed here by name. In the event that you see multiple entries, look for the listing containing "event" in the title. If you find that your controller is not listed by name, you can substitute the event number when it comes time. Now let's move on to discovering the event codes for each button of the controller by typing:
```
evtest /dev/input/event[•]
```
Make sure to replace [•] with the controllers event number, then press 'Enter'. Here you will see a printout of information regarding your controller. Wait for it to finish and you will be met with a message that reads, "Testing ... (interrupt to exit)". Now, when you press any button on your controller, a few lines of text will appear that make reference to the button's event `BTN_` name. Make a note of it's name and repeat with each button until all the names are known. After that, press your left analog stick in the up direction and you will notice that it is given an `ABS_` name. As up and down make the complete Y-Axis, both will have an identical name. The same goes for left and right that make up the X-Axis. After you note those two names, repeat the process for the right analog stick, as well as the directional pad. Depending on whether or not your controller has analog triggers, pressing them will either produce a `BTN_` name or an `ABS_` name. Also, you may find that your directional pad outputs a separate `BTN_` name for each direction rather than `ABS_` axis names. If your controller doesn't have any analog sticks or triggers, you will still be able to move forward using only the `BTN_` codes.

Now that we have all the event codes from the controller, we can begin mapping them to the virtual XBox360 controller in a command that will be added to `/etc/rc.local` so that it may launch along with RetroPie as it boots up. Below is a template that illustrates the command format. In essence, this command is simply mapping each of the event codes from the physical controller to the virtual XBox360 controller that xboxdrv will create. The specific information gathered from the steps above are marked with [•]. A legend for the virtual Xbox 360 controls can be found [here](https://s32.postimg.org/zcs0wosth/xbox.jpg).
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	&
```
You can alternatively use the controller's event number if it lacks name designation, by changing `--evdev /dev/input/by-id/[•]` to `--evdev /dev/input/event[•]`

Bluetooth controllers can potentially present a problem when assigned this way, as their event numbers will shift between powering off and back on again. However, we can assign our own named event designation by first typing:
```
udevadm info -a -n /dev/input/event[•]
```
Make a note of the 'ATTRS{name}' and then type:
```
udevadm info -q all -n /dev/input/event[•]
```
Make make a note of the 'ID_MODEL' and then type:

```
sudo nano /etc/udev/rules.d/85-jseventname.rules
```
In the resulting text field, type:
```
ATTRS{name}=="[•]", ENV{DEVNAME}=="/dev/input/event*", ENV{ID_MODEL}="[•]", SYMLINK+="/dev/input/mycontroller"
```
Make sure to replace [•] with the information we collected, then press 'ctrl+o' to save the file, 'Enter' to confirm and 'ctrl+x' to exit. After the system is rebooted, you can then reference the controller reliably with `--evdev /dev/input/mycontroller`.

If the directional pad of your controller outputs individual `BTN_` names instead of `ABS_` axis names, the command is altered to accommodate as seen below. Notice the addition of `--dpad-as-button` as well as the inclusion of individual 'BTN_' assignments marked 'du,dd,dl&dr' under `--evdev-keymap`.
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--dpad-as-button \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start,BTN_[•]=du,BTN_[•]=dd,BTN_[•]=dl,BTN_[•]=dr \
	&
```
If you're mapping a controller that doesn't have analog controls, or the full set of buttons found on an XBox360 controller, below is a SNES controller type example of how you would ignore those unused controls to prevent some software from trying to access them automatically. Here you will notice the addition of `--dpad-only`, which will ignore both sticks as well as the added argument for `--ui-axismap` and `--ui-buttonmap` where the voided buttons are defined. You can also use the `--dpad-as-button` argument and the accompanying `-evdev-keymap` direction buttons found in the example above if this controller also outputs it's Dpad as individual buttons.
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=back,BTN_[•]=start \
	--dpad-only \
	--ui-axismap lt=void,rt=void
	--ui-buttonmap tl=void,tr-void,guide=void \
	&
```
All that is really left is to add the command to `/etc/rc.local`. To do this type:
```
sudo nano /etc/rc.local
```
Press 'Enter" and paste the command into the file above "exit 0". Now press 'ctrl+o' to save the file, 'Enter' to confirm and 'ctrl+x' to exit. Seeing as how this command is run as the system boots up, you'll now need to reboot by typing:
```
sudo reboot
```
Press 'Enter' and wait for Emulation Station to load where you can then remap the controller which will now be seen as being no different from a standard XBox 360 wired Controller. If for some reason you should wish your controller to be seen as a wireless XBox360 controller, just change `--mimic-xpad` to `--mimic-xpad-wireless` in the configuration.

`------------------------------------------------------------------------------`

# **(2) Fine tuning your controller.**

As mentioned in the first section, xboxdrv can also be used to fine-tune a controller's operation in ways that aren't often found in most Linux tools. This is very important when you have a controller that misbehaves in one way or another and would be unusable without proper calibration. 

## **(2A) Analog control calibration**

You may have noticed that we've already done a bit of fine-tuning with "deadzones" in the three examples from section one. When a pressure-sensitive analog control is used, activity is reported from the controller. The problem is that many controllers, both new and old, sometimes report applied pressure when at rest. This can be due to an overly sensitive new controller or a worn out old controller. Setting a deadzone value specifies that a certain amount of pressure be applied before any activity is reported. This prevents drifting and unwanted character movement. The applied values from the examples above are recommended in the xboxdrv manual, but naturally adjustments can be made when needed.

To further adjust the accuracy of your analog controls, you can also set the minimum and maximum range of the X and Y axis of your triggers and sticks. This becomes very important to get the full range of movement from your controller, that might otherwise be hindered in some way. One example is the gate surrounding an analog stick sometimes prohibits the maximum outside movement of a joystick causing, among other things, Emulation Station to not register an up, down, left or right movement, preventing a successful map. To calibrate your analog controls we'll first need to make note of the minimum, maximum and center positions using `jstest`. To do this, drop down to the command line by pressing 'F4'. If your controller has an xboxdrv configuration applied to it you'll first need to type:
```
sudo killall xboxdrv
```
Press 'Enter' and then we will need to determine which js[•] you controller is at. To do this, type:
```
cat /proc/bus/input/devices

```
Press 'Enter' and look for the controller in the list of devices. It can be identified by it's name in the device groupings next to the line beginning with `N: Name=`. Once you find it, make a note of it's js[•] number next to the line beginning with `H: Handlers= `. After you know the js[•] number, you will then type:
```
jstest /dev/input/js[•]
```
Make sure to replace [•] with your joystick's number and press 'Enter'. You should now see the joystick testing interface. Starting with the left joystick, slowly push in the left direction until it will not move anymore. You should see numerical onscreen feedback representing the absolute minimum X-axis value. Make a note of that value and release the joystick completely. At this point, make a note of the absolute center X-axis numerical value. Then, slowly push in the right direction until it will not move anymore and make note of the absolute maximum X-axis numerical value. Repeat that process moving slowly from top, center to bottom of the Y-axis, making notes of each value. When completed, you will then repeat the entire process on the right joystick. This process can also be applied to your analog triggers as well if needed. Once all of the values are known for your analog controls, you will add them to your xboxdrv configuration formatted as: `--calibration AXIS=YourMinimumValue:YourCenterValue:YourMaximumValue`. Using the base configuration example from the first section, it would look like this in practice:
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--calibration x1=YourMinimumX1Value:YourCenterX1Value:YourMaximumX1Value,y1=YourMinimumY1Value:YourCenterY1Value:YourMaximumY1Value \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	&
```
Once this is added, each of your joysticks will benefit from the absolute full range of movement possible allowing for much finer control. If your xboxdrv configuration is invoked in `/etc/rc.local`, you'll need to reboot your system to see the changes.


## **(2B) Converting analog triggers to digital**

This next one is a quick, easy and very effective for retro-gamers. Pressure sensitive analog triggers bring an extra level of realism and control to the few games that can make use of them, such as Mame racing games. However, most retro games and console emulation software don't really benefit from analog triggers and in some cases, they can slow response time and even prevent functionality altogether. For these reasons, it is generally suggested that analog triggers be converted to digital input in almost all cases. to do this, you would simply add `--trigger-as-button` to your xboxdrv configuration. Using the base configuration example from the first section, it would look like this in practice:
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--trigger-as-button \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	&
```
Once added, the system will register any analog increase or decrease as an on/off digital button state. If your xboxdrv configuration is invoked in `/etc/rc.local`, you'll need to reboot your system to see the changes.

## **(2C) Personalizing your controller's ID name**

After fine-tuning your controller, you may want to give it a personalized ID. Outside of the novelty, this technique can be used as a tool to separate identification of multiple identical controllers in some software that can otherwise get confused when identically named controllers are discovered. To do this, you would replace `--mimic-xpad` with `--device-name "My Most Non-Non-Triumphant Controller Name Here"`. Using the base configuration example from the first section, it would look like this in practice:
```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--device-name "My Most Non-Non-Triumphant Controller Name Here" \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	&
```
Once added the entire system will identify the controller by the new name, so remapping will be necessary in Emulation Station. If your xboxdrv configuration is invoked in `/etc/rc.local`, you'll need to reboot your system to see the changes.

## **(2D) Restricting directional control to four ways**

When emulating classic video games, sometimes having a modern controller can work against you. Games like 'Burger Time' or the 'Pac-Man' series were only ever designed for 4-way directional control. This becomes a problem when using a controller with a free range of analog movement. When Pac-Man tries to turn a corner or Chef Peter Pepper tries to climb a ladder, a brief, but deadly pause often happens as a result of getting mixed directional input when the joystick hits a diagonal position. This can be eliminated in an xboxdrv control scheme by simply adding `--four-way-restrictor`. Using the base configuration example from the first section, it would look like this in practice:

```
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--four-way-restrictor
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
```
Once added, the games will perform just as fluidly as they did using their original joysticks.

`------------------------------------------------------------------------------`

# **(3) Key-Mapping For Individual Emulators**

## **(3A) Key-Mapping and Launch Fundamentals**

The foundation has been laid. Controller's have been fine-tuned. Now, we'll take a look at how to map keyboard keys and mouse movements to a controller's analog sticks and buttons for use in emulators that lack native controller support and how to launch and maintain multiple mappings accordingly. We'll be using ScummVM as an example because it's easy and it involves mapping both keyboard keys to buttons and the mouse to the analog stick. Those who have tried using the internal joystick support in ScummVM know that it leaves much to be desired. The cursor movement is shakey and you still need a keyboard to quit the program. This mapping will solve both of those problems.

If it doesn't already exist, start by creating the `runcommand-onstart.sh` file. To do this, drop down to the command line by pressing 'F4' on your keyboard, then type:

```
nano /opt/retropie/configs/all/runcommand-onstart.sh
```
Press 'Enter" and type the following:
```
#!/bin/sh
```
On a line below that, we will wrap our xboxdrv configuration for ScummVM inside a simple if/else statement, beginning with `if [ "$1" = "scummvm" ]` and ending with `fi`. When using this technique for other emulators/ports, you would of course replace "scummvm" with the appropriate name that can be found used also as the folder name for the system/port in either `/opt/retropie/configs/` or `/opt/retropie/configs/ports/`. We're also going to prevent any unsightly messages from being printed to the screen by adding `> /dev/null 2>&1` after every command that would otherwise give visual feedback. It is important to note that while troubleshooting any problems, it may become necessary to temporarily remove these particular entries so that errors that might give insight as to the cause can be seen. Below we see the full example in practice:

```
if [ "$1" = "scummvm" ]
then
sudo killall > /dev/null 2>&1 xboxdrv
sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv > /dev/null 2>&1 \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	--axismap -Y1=Y1,-Y2=Y2 \
	--ui-axismap x1=REL_X:10,y1=REL_Y:10 \
	--ui-buttonmap b=BTN_LEFT,a=BTN_RIGHT,start=KEY_F5 \
	--ui-buttonmap guide=void,x=void,y=void,lb=void,rb=void,tl=void,tr=void,lt=void,rt=void,back=void \
	--ui-axismap x2=void \
&
fi
```
Now, press 'ctrl+o' to save the file, 'Enter' to confirm and 'ctrl+x' to exit. All that is left is to make the script executable in the terminal by typing:
```
chmod +x /opt/retropie/configs/all/runcommand-onstart.sh
```
Notice that our entry begins with a sudo command to kill any other instances of xboxdrv. This is in case you have already configured your controller with a system-wide mapping from the earlier steps. We'll go over later how to re-enable that system-wide mapping automatically when the emulator shuts down so that you will be left where you started. If you have no system-wide mapping, the basic controls you have set up in Emulation Station will return once the emulator quits without any further setting. For this particular mapping, we have enabled mouse support to the left joystick, mouse left and right buttons to controller buttons 'b' and 'a', as well as mapping the 'F5' key to the controller's 'start' button so that we can bring up the menu and control the entire software from the controller. To do this, we added two new lines to our basic configuration in the form of `--ui-axismap` and `--ui-buttonmap`. 

This particular example works well for mapping a controller's left analog stick to mouse support using the `--ui-axismap` variable and can be changed to the right stick by simply altering the line to `--ui-axismap x2=REL_X:10,y2=REL_Y:10`. To change the speed of the mouse, just change the `REL_[•]:[•]` integer of the X and Y axis higher or lower than `10`. If you should ever want to map keyboard keys to an analog stick, a classic example would look like `--ui-axismap X1=KEY_A:KEY_D,Y1=KEY_W:KEY_S`, giving you the ADWS control scheme found in many classic computer titles. As far as key-mapping buttons is concerned, first you must consider which buttons are available to you. Seeing as how xboxdrv emulates a standard XBox 360 controller, you will have any of those buttons that you have already assigned to your controller in the earlier steps. If you have assigned all the buttons that are possible, you'll have access to a,b,x,y,lb,rb,lt,rt,tl,tr,start,back and guide. The placement of these buttons can be seen [here](https://s32.postimg.org/zcs0wosth/xbox.jpg). By using the `--ui-buttonmap` variable, you can then map any one of the buttons to a key using the format above. To discover all the possible keyboard keys that are available to you, type `/opt/retropie/supplementary/xboxdrv/bin/xboxdrv --help-key`. Finally, you'll notice that their are two more lines added with the `--ui-axismap` and `--ui-buttonmap` variables that are solely responsible for voiding the unused control elements. This is optional, but it will make the control scheme cleaner by eliminating the possibility of those elements conflicting in any way.

Now we need to ensure that or xboxdrv mapping is torn down as the emulator/port exits back to Emulation station. We'll do this by adding `sudo killall > /dev/null 2>&1 xboxdrv` to `/opt/retropie/configs/all/runcommand-onend.sh`. Also, for those who have a system-wide xboxdrv mapping that should be restored afterward, we'll copy the same configuration from your `/etc/rc.local` to '/opt/retropie/configs/all/runcommand-onend.sh' as well. If the `runcommand-onend.sh` file doesn't exist yet, drop to the command line and type:
```
nano /opt/retropie/configs/all/runcommand-onend.sh
```
Press 'Enter" and type the following:
```
#!/bin/sh
```
On a line below, you can now add the `killall` command, followed by the global xboxdrv command you previously added to `/etc/rc.local` if applicable. To continue to keep things nice and silent, we'll add `> /dev/null 2>&1` to that original command. Using the base configuration example from the first section, it would look like this in practice:
```
sudo killall > /dev/null 2>&1 xboxdrv
/opt/retropie/supplementary/xboxdrv/bin/xboxdrv > /dev/null 2>&1 \
	--evdev /dev/input/by-id/[•] \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--deadzone-trigger 15% \
	--deadzone 4000 \
	--mimic-xpad \
	--evdev-absmap ABS_[•]=x1,ABS_[•]=y1,ABS_[•]=x2,ABS_[•]=y2,ABS_[•]=lt,ABS_[•]=rt,ABS_[•]=dpad_x,ABS_[•]=dpad_y \
	--evdev-keymap BTN_[•]=a,BTN_[•]=b,BTN_[•]=x,BTN_[•]=y,BTN_[•]=lb,BTN_[•]=rb,BTN_[•]=tl,BTN_[•]=tr,BTN_[•]=guide,BTN_[•]=back,BTN_[•]=start \
	&
```
Now, press 'ctrl+o' to save the file, 'Enter' to confirm and 'ctrl+x' to exit. All that is left is to make the script executable in the terminal by typing:
```
chmod +x /opt/retropie/configs/all/runcommand-onend.sh
```
To fully round out this section on key-mapping, it should be mentioned that in some scenarios, the keyboard that xbmc virtualizes may not be recognized as being a keyboard by the software you intend to use it with. In this situation, you can create a udev rule that will authenticate the input as being from an actual keyboard at a system level, allowing it to function anywhere. To add this udev rule, drop to the command line and type:
```
sudo nano /etc/udev/rules.d/99-xboxdrv.rules
```
Press 'Enter" and type the following:
```
SUBSYSTEM=="input", ATTRS{name}=="Microsoft X-Box 360 pad - Keyboard Emulation", GROUP="users", MODE="0666", ENV{ID_INPUT_KEYBOARD}="1"
```
Now press 'ctrl+o' to save the file, 'Enter' to confirm and 'ctrl+x' to exit. The name "Microsoft X-Box 360 pad - Keyboard Emulation" is dependent on the use of the `--mimic-xpad` variable used in your xboxdrv command. If you have customized that name using the `--device-name` variable instead, as seen in the earlier example, it would then be replaced with "My Most Non-Non-Triumphant Controller Name Here - Keyboard Emulation".

## **(3B) Expanding Launch Capabilities**

For mapping one or two systems, the above method is the simplest approach. However, it can be a bit unwieldy when mapping a large number of systems. What follows is an alternate method that again utilizes the `runcommand-onstart.sh` shell script, now based on a unified case statement designed specifically for mapping multiple systems. In addition, all the xboxdrv parameters are assigned to variables, making the case statement easier to read.

If it doesn't already exist, start by creating the `runcommand-onstart.sh` file:

```
nano /opt/retropie/configs/all/runcommand-onstart.sh
```

The following is just an example, everyone should change the configuration based on their own controller

```
#!/bin/sh
## Uncomment one or all of the following if you need to find some information about the emulator or roms
## Name of the emulator
#echo $1 >> /dev/shm/runcommand.log

## Name of the software used for running the emulation
#echo $2 >> /dev/shm/runcommand.log

## Name of the rom
#echo $3 >> /dev/shm/runcommand.log

##Executed command line
#echo $4 >> /dev/shm/runcommand.log


### The FUN begins
#Get ROM name striping full path
rom="${3##*/}"

### Set variables for your joypad and emulator
### Basic Configuraions - Standard controller mappings 
basicPS3="sudo /opt/retropie/supplementary/xboxdrv/bin/xboxdrv >/dev/null \
	--evdev /dev/input/event2 \
	--silent \
	--detach-kernel-driver \
	--force-feedback \
	--mimic-xpad \
	--dpad-as-button \
	--trigger-as-button \
	--evdev-absmap ABS_X=x1,ABS_Y=y1,ABS_Z=x2,ABS_RX=y2 \
	--evdev-keymap KEY_#302=a,KEY_#301=b,BTN_DEAD=x,KEY_#300=y,BTN_THUMB=tl,BTN_THUMB2=tr,BTN_BASE5=lb,BTN_BASE6=rb,BTN_BASE3=lt,BTN_BASE4=rt,BTN_TRIGGER=back,BTN_TOP=start,BTN_SOUTH=guide,BTN_TOP2=du,BTN_PINKIE=dr,BTN_BASE=dd,BTN_BASE2=dl
	--calibration x1=-32767:0:32767,y1=-32767:0:32767,x2=-32767:0:32767,y2=-32767:0:32767"


### Extended Configurations
### Specific emulator configuration or any other parameters you will need only for some emulators
scummVM="--axismap -Y1=Y1,-Y2=Y2 \
	--ui-axismap x1=REL_X:10,y1=REL_Y:10 \
	--ui-buttonmap a=BTN_LEFT,b=BTN_RIGHT,start=KEY_F5,back=KEY_ESC \
	--ui-buttonmap guide=void,x=void,y=void,lb=void,rb=void,tl=void,tr=void,lt=void,rt=void,back=void \
	--ui-axismap x2=void"

amiga="--axismap -Y1=Y1,-Y2=Y2 \
	--ui-axismap x2=REL_X:1,y2=REL_Y:1 \
	--ui-axismap x1=KEY_LEFT:KEY_RIGHT,y1=KEY_DOWN:KEY_UP \
	--ui-buttonmap du=KEY_UP,dd=KEY_DOWN,dl=KEY_LEFT,dr=KEY_RIGHT \
	--ui-buttonmap lt=BTN_LEFT,rt=BTN_RIGHT,start=KEY_ESC,back=KEY_LEFTCTRL,y=KEY_SPACE,a=KEY_LEFTCTRL,b=KEY_LEFTALT,x=KEY_LEFTSHIFT \
	--ui-buttonmap guide=void,tl=void,lt=void,rt=void,back=void \
	--ui-axismap x2=void"

fourway="--four-way-restrictor"

invert="--ui-buttonmap du=KEY_DOWN,dd=KEY_UP"

### Kill Command
xboxkill="sudo killall >/dev/null xboxdrv"

### Execute the driver with the configuration you need
# $1 is the name of the emulation, not the name of the software used
# it is intellivision not jzintv
case $1 in

	mame-libretro)
	;;

	fba)
		case $rom in
			"amidar.zip"|"atetris.zip"|"puckman.zip") # Configuration used only for these ROMs
				$xboxkill
				joycommand="$basicPS3 $fourway &"
				eval $joycommand
			;;
			*) # Configuration for every other ROMs on this emulator
				$xboxkill
				joycommand="$basicPS3 &"
				eval $joycommand
			;;
		esac
	;;

	daphne)
	;;

	scummvm)
		$xboxkill
		joycommand="$basicPS3 $scummVM &"
		eval $joycommand
	;;

	amiga)
		$xboxkill
		joycommand="$basicPS3 $amiga &"
		eval $joycommand
	;;

	intellivision)
	;;
esac
```

We assign to the `joycommand` variable, the list of variables that contains the parameters we need for example `joycommand="BasicVAR var1 var2 var3 $"`. The Basic variables must be the first, and `&` must be the last.

Next, we make the script executable:

```
sudo chmod +x /opt/retropie/configs/all/runcommand-onstart.sh
```

For some emulators we could face some problem, i have a PS3 controller recognized as input device `event2`, when i execute xboxdrv the controller is recognized as input device `event3`. The system now see 2 controller device, the PS3 as controller with id 0 and an Xbox360 controller with id 1, for the emulator you are now using the controller for player2 and this will cause some problem, for example you can only start a 2 players game, you can't quit the emulation pushing 'select+start'. To solve the problem we have to specify on `retroarch.cfg` the id of the controller used by player1 and player2.

This is the configuration for Final Burn Alpha, we have to add `input_playerx_joypad_index = "x"` for every controller between `input_remapping_directory = "/opt/retropie/configs/fba/"` and `#include "/opt/retropie/configs/all/retroarch.cfg"` where the first X is the player number, and the secon X is the controller ID.

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = "/opt/retropie/configs/fba/"

input_player1_joypad_index = "1"
input_player2_joypad_index = "0"
input_player2_analog_dpad_mode = 1

#include "/opt/retropie/configs/all/retroarch.cfg"

```

If you want this configuration for every retroarch emulators, you have to edit `nano /opt/retropie/configs/all/retroarch.cfg`

Now we need to kill xboxdrv when we exit from the emulator, we do this with the onend script

```
nano /opt/retropie/configs/all/runcommand-onend.sh
```

```
#!/bin/sh
sudo killall >/dev/null xboxdrv
```

and make it executable

```
sudo chmod +x /opt/retropie/configs/all/runcommand-onend.sh
```

`------------------------------------------------------------------------------`