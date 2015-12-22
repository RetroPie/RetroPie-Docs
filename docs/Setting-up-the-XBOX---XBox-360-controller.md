## Automatic Configuration

The easiest way to set this up is to use the "Xbox / Xbox 360 gamepad driver" option in the Setup / Configuration menu of the retropie-setup script.

This will install the driver and add a start-up configuration in /etc/rc.local

Alternatively if you prefer you can manually install it..

## Manual Configuration

RetroPie 3.3 contains a newer xboxdrv at /opt/retropie/supplementary/xboxdrv/bin/xboxdrv - which is preferable over the older Debian package. On older RetroPie images you can install the Debian package.

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

## Xbox 360 controller glitchy?

According to [this post](https://github.com/petrockblog/RetroPie-Setup/issues/214#issuecomment-21796016) it might help to add the line ```dwc_otg.speed=1```to the file ```/boot/cmdline.txt```.

#### *Outdated* optional manual configs


``
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