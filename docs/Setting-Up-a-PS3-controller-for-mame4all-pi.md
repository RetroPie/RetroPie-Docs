The PS3 controller works out of the box for most emulators in version 2.2 of the Retropie image. This is not the case for mame4all-pi as the code rejects controllers with more than 6 axes. Here is the fix.


1. Edit the file minimal.cpp found in the mame4all-pi/src/rpi directory to comment the lines of code that are rejecting the PS3 controller. Run the command below to edit the file.

    `sudo nano /opt/retropie/emulators/mame4all-pi/src/rpi/minimal.cpp`

  Comment out lines 168 to 174 so that the code appears as 

      //   if (SDL_JoystickNumAxes(myjoy[i]) > 6)
      //   {
      //      SDL_JoystickClose(myjoy[i]);
      //      myjoy[i]=0;
      //      logerror("Error detected invalid joystick/keyboard\n");
      //      break;
      //  } 

  Save and exit.

2. Recompile by going to the mame4all directory

      `cd /opt/retropie/emulators/mame4all-pi/ ` 
      
  and running the following command.

  `make`

  This process can several hours.

  Errors during the recompile may suggest that some packages need to be installed. Check the [source code](http://code.google.com/p/mame4all-pi/) to see what may be missing. The Retropie 2.2 image should recompile without problems.

3. Configure the PS3 controller using the Mame menu accessed by pressing the TAB key on a keyboard. If any changes are not being made, then check the following.

   i) Check that there is a folder cfg in the mame4all-pi directory. If not, then create one.

  ii) If the cfg folder exists, then check who owns the folder by running the command

  `ls -ld /opt/retropie/emulators/mame4all-pi/cfg`

  For changes to be saved, the user should be pi, not root. The output when this command is run should be similar to below.

  `drwxr-xr-x 2 pi pi 4096 Jul 8 14:21 /opt/retropie/emulators/mame4all-pi/cfg`

  If root is the owner, then change the user to pi with the following command.

  `sudo chown -R pi:pi /opt/retropie/emulators/mame4all-pi/cfg`


Finally credit where it's due.

To penguin.. for suggesting the fix at [Issue 33 PS3 controllers not working in UI or in-game](https://code.google.com/p/mame4all-pi/issues/detail?id=33).

To nemo93 for the easy fix for saving key mappings at [Retropie Forum](http://blog.petrockblock.com/forums/topic/no-writing-permission-for-retroarch-cfg/#post-12219).