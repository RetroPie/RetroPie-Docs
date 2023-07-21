### Making RetroPie identify 2 players instead of one with the Xin-Mo  
  
Add the following to `/boot/cmdline.txt` -- just add a space to the end of the existing entry, so it is all on one line):

`usbhid.quirks=0x16c0:0x05e1:0x040`
  
The first two numbers are the vendor ID `16c0` and product ID `05e1`.
If you have a **Juyao Dual Arcade**, it is the same device, but the vendor ID is `0314` and the product ID is `0328`:

`usbhid.quirks=0x0314:0x0328:0x040`

An alternate configuration method is to create a kernel module configuration file for the `usbhid` driver. Create a new file by running `sudo nano /etc/modprobe.d/rp-usbhid-quirks.conf` (the file name is not important, but the file extension is), with the contents
``` 
options usbhid quirks=0x0314:0x0328:0x040
```
This method works for both Raspberry Pi and PC based installations. 

You can find your Vendor/Product IDs by running the `lsusb` command from the command line.  
  
More details in these threads

* http://blog.petrockblock.com/forums/topic/autofire-on-the-axis/page/5/#post-104325
* http://blog.petrockblock.com/forums/topic/autofire-on-the-axis/page/5/#post-104433  
* http://blog.petrockblock.com/forums/topic/how-to-get-xin-mo-dual-arcade-working-with-retropie-easy-guide/

### Older Info

If you have troubles with the Xin-Mo driver you can find a guide for patching the driver at http://ithink.ch/blog/2013/09/08/patching_the_linux_kernel_to_install_the_xin-mo_dual_arcade_driver_on_a_raspberry_pi.html.

The troubles I had configuring a joystick with the Xin-Mo controller, besides the previous one:

**MAME4ALL-PI (MAME)**

The MAME emulator only reads 16 buttons of the joysticks, so only use the first 16 button inputs of the controller (from 0 to 15). So if you don't have many buttons (6 by player, 2 Start and 2 service) work alright. You can make the MAME4ALL-PI to use more buttons by modifying the source and compiling it, but it's not an easy task.

**PIFBA (NeoGeo and other Arcade)**

The emulator expects one controller for each player (e.g. 2 UBS controllers), as the Xin-Mo is detected as only one, the PIFBA only loads the Player 1 controls (no matter what you have on the fba2x.cfg).
So in order to make it work I had to edit the source (not in the bets way, but it works), the following files:
*     /rpi/fba_player.cpp
*     /rpi/gp2xsdk.cpp
*     /rpi/gp2xsdk.h (maybe its not required, only for the default values)

fba_player.cpp: To force **do_keypad()** to create 2 FBA_KEYPAD, I forced joyCount=2, so the for loop executes 2 times

gp2xsdk.cpp:
In **pi_joystick_read(int which1)** I changed all joy_buttons[1] to joy_buttons[0], because both players are in the first joystick (0). 
Also, the movements for the second joystick axis (joyaxis_LR_2 and joyaxis_UD_2) are not defined, so you have to add them in **pi_process_events (void)**, inside **case SDL_JOYAXISMOTION:** like this:

>             case SDL_JOYAXISMOTION:
>                                 if(event.jaxis.axis == joyaxis_LR) {
>                                         if(event.jaxis.value > -10000 && event.jaxis.value < 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_LR] = CENTER;
>                                         else if(event.jaxis.value > 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_LR] = RIGHT;
>                                         else
>                                                 joy_axes[event.jbutton.which][joyaxis_LR] = LEFT;
>                                 }
>                                 if(event.jaxis.axis == joyaxis_UD) {
>                                         if(event.jaxis.value > -10000 && event.jaxis.value < 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_UD] = CENTER;
>                                         else if(event.jaxis.value > 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_UD] = DOWN;
>                                         else
>                                                 joy_axes[event.jbutton.which][joyaxis_UD] = UP;
>                                 }
>                                 if(event.jaxis.axis == joyaxis_LR_2) {
>                                        if(event.jaxis.value > -10000 && event.jaxis.value < 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_LR_2] = CENTER;
>                                         else if(event.jaxis.value > 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_LR_2] = RIGHT;
>                                         else
>                                                 joy_axes[event.jbutton.which][joyaxis_LR_2] = LEFT;
>                                 }
>                                 if(event.jaxis.axis == joyaxis_UD_2) {
>                                         if(event.jaxis.value > -10000 && event.jaxis.value < 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_UD_2] = CENTER;
>                                         else if(event.jaxis.value > 10000)
>                                                 joy_axes[event.jbutton.which][joyaxis_UD_2] = DOWN;
>                                         else
>                                                 joy_axes[event.jbutton.which][joyaxis_UD_2] = UP;
>                                 }
>                 break;