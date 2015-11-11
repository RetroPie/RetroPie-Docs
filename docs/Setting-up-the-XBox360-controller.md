## initial install

**xboxdrv** must be installed for using xbox360 controllers with your pi:

install it by running

    sudo apt-get install xboxdrv

**Then you must choose one of the 3 methods below**


### 1 - Multiples instances of xboxdrv

You have to launch multiple instances of xboxdrv (one for each controller)

For example we can edit the file **/etc/rc.local** to start instances of xboxdrv during boot

Here is an example of what to insert in **/etc/rc.local** for 4 wireless pads (put this just before **exit 0**):

    xboxdrv --trigger-as-button --wid 0 --led 2 --deadzone 4000 --silent &
    sleep 1
    xboxdrv --trigger-as-button --wid 1 --led 3 --deadzone 4000 --silent &
    sleep 1
    xboxdrv --trigger-as-button --wid 2 --led 4 --deadzone 4000 --silent &
    sleep 1
    xboxdrv --trigger-as-button --wid 3 --led 5 --deadzone 4000 --silent &

(replace the `--wid` by `--id` if you use wired controllers)
You **must** swich-on your pads before booting the raspberry.

Notice the `sleep 1` between each instance: this prevents the RPi from setting random controllers with random led status; adjust timing if necessary.

### 2 - Single command line

Another way is to specify this single command :

    xboxdrv -D i 0 --next-controller -i 1 --next-controller -i 2 --next-controller -i 3 --deadzone 4000 --dbus disabled &

### 3 - init script

The third possibility, you can use an init.d script with the daemon _-D_ Option. Save the follwing content to **/etc/init.d/xboxdrv**:
```
#! /bin/bash
### BEGIN INIT INFO
# Provides:          xbox-controller
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start XBOX Controller Service
# Description:       Start the xboxdrv daemon with several options
#                    support up to 4 Controllers
### END INIT INFO

# Author: MasteRehm

PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="XBOX Controller Service"
NAME=xboxdrv
DAEMON=/usr/bin/$NAME
DAEMON_ARGS="-D -d --deadzone 4000 --dbus disabled --detach"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.2-14) to ensure that this file is present
# and status_of_proc is working.
. /lib/lsb/init-functions

do_start()
{
        if [ $CONTROLLER_NUM -gt 4 ] ; then
                echo -e "\n$CONTROLLER"; exit 1;
        fi
        start-stop-daemon -S -q -x $DAEMON -- $DAEMON_ARGS $CONTROLLER

# -- This workaround only works with 4 controllers connected.  It also is creating a name that
# does not match the minor device node.

#        # Workaround: xboxdrv daemon creates /dev/input/js[4-7] device files, if /dev/input/js[0-3] created on startup.
#        if [ -x /usr/bin/rename ]; then
#                sleep 1
#                if [[ `ls /dev/input/js*` =~ /dev/input/js[4-7] ]]; then rename 's/js4/js0/;s/js5/js1/;s/js6/js2/;s/js7/js3/' /dev/input/js*; fi
#        fi

# Rather than renaming files, it's better to clear the existing ones by stopping the driver
# and then when you start it again, everything will be correct.

	sleep 3
	do_stop
	sleep 3
        start-stop-daemon -S -q -x $DAEMON -- $DAEMON_ARGS $CONTROLLER
}


do_stop()
{
    start-stop-daemon -K -o -q -x $DAEMON
    sleep 1
}

case "$1" in
  start)
    log_daemon_msg "Starting $DESC" "$NAME"
    do_start
     status=$?
    log_end_msg $status
    ;;
  stop)
    log_daemon_msg "Stopping $DESC" "$NAME"
    do_stop
     status=$?
    log_end_msg $status
    ;;
  status)
    status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
    ;;
  restart)
    log_daemon_msg "Restarting $DESC" "$NAME"
    do_stop
    case "$?" in
      0|1)
        do_start
        case "$?" in
            0) log_end_msg 0 ;;
            1) log_end_msg 1 ;; # Old process is still running
            *) log_end_msg 1 ;; # Failed to start
        esac
        ;;
      *)
        # Failed to stop
        log_end_msg 1
        ;;
    esac
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|status|restart}" >&2
    exit 3
    ;;
esac
```
`sudo chmod +x /etc/init.d/xboxdrv`  
`sudo update-rc.d xboxdrv start 90 2 3 4 5 stop 90 0 1 6`  
You will also need a default configuration file. Save the following content to **/etc/default/xboxdrv**:
```
# How many Controllers? (support up to 4 Controllers)
CONTROLLER_NUM=2

case $CONTROLLER_NUM in
    1) CONTROLLER="-w 0 -l 2 --trigger-as-button --dpad-as-button"
    ;;
    2) CONTROLLER="-w 0 -l 2 --trigger-as-button --dpad-as-button --next-controller -w 1 -l 3 --trigger-as-button --dpad-as-button"
    ;;
    3) CONTROLLER="-w 0 -l 2 --trigger-as-button --dpad-as-button --next-controller -w 1 -l 3 --trigger-as-button --dpad-as-button --next-controller -w 2 -l 4 --trigger-as-button --dpad-as-button"
    ;;
    4) CONTROLLER="-w 0 -l 2 --trigger-as-button --dpad-as-button --next-controller -w 1 -l 3 --trigger-as-button --dpad-as-button --next-controller -w 2 -l 4 --trigger-as-button --dpad-as-button --next-controller -w 3 -l 5 --trigger-as-button --dpad-as-button"
    ;;
    *) CONTROLLER="incorrect amount of controller specified"
    ;;
esac
```
To specifiy the amount of controller, edit the variable CONTROLLER_NUM. If you have a wired controller, replace all "-w" occurences with "-i".

It is generally advisable to use the daemon mode, 'cause it uses less CPU and RAM instead of several xboxdrv processes for each controller.

## RetroPie configuration

At this point you can test your pads with `jstest /dev/input/js[0-3]` to see if everything works well.

After reboot when your controllers are detected, you have to configure RetroPie to use them:

Go to the `retroarch-joyconfig` folder (binary for configuring joypads for RetroArch);

By default (if you followed the install tutorial for the latest version):

    cd /opt/retropie/emulators/retroarch/

Before we start, please make sure the following folder has read/write permissions.
We use /opt/retropie/configs/all/ as the base directory for the configuration files.

    sudo chmod +rw /opt/retropie/configs/all/

Then you have to configure each controller ( For example just use the first line if you have only 1 controller):

    ./retroarch-joyconfig -o /opt/retropie/configs/all/p1.cfg -p 1 -j 0
    <follow instructions>
    ./retroarch-joyconfig -o /opt/retropie/configs/all/p2.cfg -p 2 -j 1
    <follow instructions>
    ./retroarch-joyconfig -o /opt/retropie/configs/all/p3.cfg -p 3 -j 2
    <follow instructions>
    ./retroarch-joyconfig -o /opt/retropie/configs/all/p4.cfg -p 4 -j 3
    <follow instructions>

( **-o** for output file, **-p** for player, **-j** for joystick id )

After this you will get 4(or less depending) cfg files to add to your default `/opt/retropie/configs/all/retroarch.cfg` config file:

    sudo cat /opt/retropie/configs/all/p*.cfg >> /opt/retropie/configs/all/retroarch.cfg

(if this don't have permissions you can do a `sudo chown pi.pi /opt/retropie/configs/all/retroarch.cfg; sudo chmod 644 /opt/retropie/configs/all/retroarch.cfg` before)

If your config is not working well, delete the joypad configuration lines in `/opt/retropie/configs/all/retroarch.cfg` before doing anything.

(Delete the lines located at the bottom of the file, starting with line `input_player1_joypad_index = "0"`)

Now just reboot and voila !

## Troubleshooting
If your controllers are connecting and you can use them from within EmulationStation, but *cannot* use them from inside the emulators, do the following:

* Make sure you do not have conflicting xboxdrv configurations. If you installed the daemon, make sure you don't have another instance of the service running (`ps ax | grep xboxdrv` will show you this). Things may not work correctly if you have the daemon service (option 3 from above) *AND* something in `/etc/rc.local`. (There may be a message at startup that indicates a `LIBUSB` error if this is the case). 
* When training the controllers using `retroarch-joyconfig`, make sure that you exit EmulationStation. 
* Use the `retropie_setup.sh` script to train your controller. 

## Xbox 360 controller glitchy?

According to [this post](https://github.com/petrockblog/RetroPie-Setup/issues/214#issuecomment-21796016) it might help to add the line ```dwc_otg.speed=1```to the file ```/boot/cmdline.txt```.

#### *Outdated* optional manual configs


```
### Emulationstation adjustments
There are a few adjustments for emulationstation. In my case the input for my Xbox 360 Controller and some entries for the systems, aka emulators.  
**`/home/pi/.emulationstation/es_input.cfg`**
xml
<?xml version="1.0"?>
<inputList>
    <inputConfig type="keyboard" />
    <inputConfig type="joystick" deviceName="Xbox Gamepad (userspace driver)">
        <input name="a" type="button" id="4" value="1" />
        <input name="b" type="button" id="5" value="1" />
        <input name="down" type="button" id="1" value="1" />
        <input name="left" type="button" id="2" value="1" />
        <input name="menu" type="button" id="13" value="1" />
        <input name="pagedown" type="button" id="11" value="1" />
        <input name="pageup" type="button" id="10" value="1" />
        <input name="right" type="button" id="3" value="1" />
        <input name="select" type="button" id="8" value="1" />
        <input name="up" type="button" id="0" value="1" />
    </inputConfig>
    <inputConfig type="keyboard">
        <input name="a" type="key" id="13" value="1" />
        <input name="b" type="key" id="8" value="1" />
        <input name="down" type="key" id="274" value="1" />
        <input name="left" type="key" id="276" value="1" />
        <input name="menu" type="key" id="109" value="1" />
        <input name="pagedown" type="key" id="281" value="1" />
        <input name="pageup" type="key" id="280" value="1" />
        <input name="right" type="key" id="275" value="1" />
        <input name="select" type="key" id="108" value="1" />
        <input name="up" type="key" id="273" value="1" />
    </inputConfig>
</inputList>


Button  | Configname
--------|-----------
A       | a
B       | b
DPdown  | down
DPup    | up
DPleft  | left
DPright | right
Start   | menu
LB      | select
LT      | pageup
RT      | pagedown

_DP = DigiPad_

***
### Xbox 360 Controller button configuration for retroarch and final burn alpha
**`/home/pi/RetroPie/configs/all/retroarch.cfg`**
bash
#Player 1
input_player1_joypad_index = 0
input_player1_b_btn = 6
input_player1_a_btn = 4
input_player1_y_btn = 7
input_player1_x_btn = 5
input_player1_l_btn = 10
input_player1_r_btn = 11
input_player1_start_btn = 13
input_player1_select_btn = 12
input_player1_up_btn = 0
input_player1_down_btn = 1
input_player1_left_btn = 2
input_player1_right_btn = 3
input_exit_emulator_btn = 15
input_menu_toggle_btn = 16

#Player 2
input_player2_joypad_index = 1
input_player2_b_btn = 6
input_player2_a_btn = 4
input_player2_y_btn = 7
input_player2_x_btn = 5
input_player2_l_btn = 10
input_player2_r_btn = 11
input_player2_start_btn = 13
input_player2_select_btn = 12
input_player2_up_btn = 0
input_player2_down_btn = 1
input_player2_left_btn = 2
input_player2_right_btn = 3

_input exit emulator_ to exit the emulator and return to emulationstation._input menu toggle_ to show the retroarch menu (e.g. to set the aspect ratio, save/load the game, etc.)

**`/home/pi/RetroPie/emulators/pifba/fba2x.cfg`** (or **`/opt/retropie/emulators/pifba/fba2x.cfg`** in some versions)
bash
[Joystick]
A_1=4
B_1=5
X_1=6
Y_1=7
L_1=10
R_1=11
START_1=13
SELECT_1=12
#Joystick axis
JA_LR=0
JA_UD=1

#player 2 button configuration
A_2=4
B_2=5
X_2=6
Y_2=7
L_2=10
R_2=11
START_2=13
SELECT_2=12
#Joystick axis
JA_LR_2=0
JA_UD_2=1

Up to now, I didn't figure out, how to change the configuration from the analog sticks to the digipad. To exit the emulator, press START and SELECT together.
***
```