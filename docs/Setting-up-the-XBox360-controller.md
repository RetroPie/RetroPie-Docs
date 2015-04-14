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
        if [ $CONTROLLER_NUM -gt 4 ]; then
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

## Xbox 360 controller glitchy?

According to [this post](https://github.com/petrockblog/RetroPie-Setup/issues/214#issuecomment-21796016) it might help to add the line ```dwc_otg.speed=1```to the file ```/boot/cmdline.txt```.