**xboxdrv** must be installed for using xbox360 controllers with your pi:

install it by running

    sudo apt-get install xboxdrv

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

After reboot when your controllers are detected, you have to configure RetroPie to use them:

Go to the `retroarch-joyconfig` folder (binary for configuring joypads for RetroArch);

By default (if you followed the install tutorial):

    cd ~/RetroPie/emulators/RetroArch/tools

Then you have to configure each controller ( For example just use the first line if you have only 1 controller):

    ./retroarch-joyconfig -o p1.cfg -p 1 -j 0
    <follow instructions>
    ./retroarch-joyconfig -o p2.cfg -p 2 -j 1
    <follow instructions>
    ./retroarch-joyconfig -o p3.cfg -p 3 -j 2
    <follow instructions>
    ./retroarch-joyconfig -o p4.cfg -p 4 -j 3
    <follow instructions>

( **-o** for output file, **-p** for player, **-j** for joystick id )

After this you will get 4(or less depending) cfg files to add to your default `RetroPie/configs/all/retroarch.cfg` config file:

    sudo cat p*.cfg >> RetroPie/configs/all/retroarch.cfg

(if this don't have permissions you can do a `sudo chmod 777 RetroPie/configs/all/retroarch.cfg` before)

If your config is not working well, delete the joypad configuration lines in `RetroPie/configs/all/retroarch.cfg` before doing anything.

(Delete the lines located at the bottom of the file, starting with line `input_player1_joypad_index = "0"`)

Now just reboot and voila !