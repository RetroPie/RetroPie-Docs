# Setting up an 8BitDo Bluetooth controller
![8BitDo Logo](http://www.8BitDo.com/images/Logo-white.svg)

This guide will show how to use an 8BitDo Bluetooth controller with RetroPie.

Please see the [8BitDo support page](http://support.8BitDo.com) for details on how to upgrade the firmware. Before you upgrade your firmware or attempt to register your controller, please make sure your controller is fully charged.

## A Note about the 8BitDo Zero controller

When pairing a 8BitDo Zero controller, make sure you start the controller by pressing _R_ + _Start_.

It also may help to reset the controller by holding down the select button for 8 seconds if this does not work. Please note that using the _R+START_ mode does result in different values for the buttons themselves so it may or may not function properly if started under any different mode. The Zero controller may also need enabling the _8BitDo hack_ option (see step 4 below).


## Guide to add your controller

1. Run the RetroPie setup script, either through the Emulation Station menu option or via the command line.
If you want to run this via the command line, quit Emulation Station by pressing F4 on the keyboard and type this at the command line:
```  shell
sudo $HOME/RetroPie-Setup/retropie_setup.sh
```

2. Choose the **Configuration / tools** menu

3. Choose the **bluetooth - Configure Bluetooth Devices** menu

4. Make sure the hack option is turned **off**
You need to make sure your controller is running the latest firmware version.

5. Make sure your controller is powered on and is set to pairing mode.

6. Choose the **Pair and connect to Bluetooth Device** from the menu

7. You will then see the **Searching** screen, that will result in a list of nearby Bluetooth devices.
 It may be the case that the first time the results are returned, the name of the controller doesn't show, or that the MAC address doesn't show at all. If that's the case, you can either select the device if you know the MAC or search again.

8. After it has successfully detected the the controller, select it from the list and then press **OK** to pair the controller.

9. Choose the **DisplayYesNo** option to complete the registration process.

10. Registration of the 8BitDo controller is complete and your blue LED lights should now be solid on (the FC30 Pro will glow).

11. _(optional and mostly not needed)_ Setup the _udev_ rule in order for EmulationStation to "see" the controller when you restart your Raspberry Pi.
This then adds the rule to the file specified, you don't need to manually take any extra steps here.
As indicated, you will need to reboot after completing these steps to make sure all the changes have taken effect.


12. Configure the controller for EmulationStation and the emulators. Press Start in Emulation Station using your non-8BitDo/other controller and choose the *Configure Input* menu option.
You should see that EmulationStation can now see your 8BitDo controller and can perform the usual [Input Configuration](Controller-Configuration) steps to configure the controller.

The process will have written various controller configuration files for you.
The main RetroArch controller profile file will be saved in 
`/opt/retropie/configs/all/retroarch-joypads/`

Here are some examples of the configuration file that would be written.

* **FC30 Pro**

``` ini
# Generated with RetroPie 4.02
# FC30 Pro with firmware 1.69

input_device = "8Bitdo FC30 Pro"
input_driver = "udev"
input_r_y_plus_axis = "+3"
input_l3_btn = "13"
input_r_x_minus_axis = "-2"
input_l_btn = "6"
input_load_state_btn = "6"
input_l2_btn = "8"
input_start_btn = "11"
input_exit_emulator_btn = "11"
input_l_y_minus_axis = "-1"
input_up_btn = "h0up"
input_r_y_minus_axis = "-3"
input_a_btn = "0"
input_b_btn = "1"
input_reset_btn = "1"
input_down_btn = "h0down"
input_l_x_plus_axis = "+0"
input_l_y_plus_axis = "+1"
input_r_btn = "7"
input_save_state_btn = "7"
input_r2_btn = "9"
input_r3_btn = "14"
input_right_btn = "h0right"
input_state_slot_increase_btn = "h0right"
input_x_btn = "3"
input_menu_toggle_btn = "3"
input_select_btn = "10"
input_enable_hotkey_btn = "10"
input_l_x_minus_axis = "-0"
input_y_btn = "4"
input_left_btn = "h0left"
input_state_slot_decrease_btn = "h0left"
input_r_x_plus_axis = "+2"
```

* **SFC30**
``` ini
# Generated with RetroPie 4.02
# SFC30 with firmware 2.68

input_device = "8Bitdo SFC30 GamePad"
input_driver = "udev"
input_l_btn = "6"
input_load_state_btn = "6"
input_start_btn = "11"
input_exit_emulator_btn = "11"
input_up_axis = "-1"
input_a_btn = "0"
input_b_btn = "1"
input_reset_btn = "1"
input_down_axis = "+1"
input_r_btn = "7"
input_save_state_btn = "7"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "3"
input_menu_toggle_btn = "3"
input_select_btn = "10"
input_enable_hotkey_btn = "10"
input_y_btn = "4"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
```

* **SNES30**
``` ini 
input_device = "8Bitdo SNES30 GamePad"
input_driver = "udev"
input_start_btn = "11"
input_exit_emulator_btn = "11"
input_up_axis = "-1"
input_a_btn = "0"
input_b_btn = "1"
input_reset_btn = "1"
input_down_axis = "+1"
input_r_btn = "7"
input_right_axis = "+0"
input_state_slot_increase_axis = "+0"
input_x_btn = "3"
input_menu_toggle_btn = "3"
input_select_btn = "10"
input_enable_hotkey_btn = "10"
input_y_btn = "4"
input_left_axis = "-0"
input_state_slot_decrease_axis = "-0"
input_l2_btn = "17"
input_load_state_btn = "6"
input_save_state_btn = "7"
```

## Video Guide

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/e2We6AElqg8" title="RetroPie 4: Adding an 8BitDo Bluetooth Controller (August 2016)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; allowfullscreen"></iframe>

## Firmware Versions for 8BitDo controllers

 8BitDo have an update application that performs the firmware update on the supported controllers. The updater runs on Windows and macOS only and will connect via an USB connected controller to perform the update.

 Firmware for 8BitDo controller has been added to the [fwupdmgr](https://github.com/fwupd/fwupd) Linux utility using the _ebitdo_ plugin, but since 8BitDo have stopped publishing the firmware files sometimes around 2021, the best option to update the firmware on a controller is using the utility provided by 8BitDo.

## Troubleshooting

* Please make sure to update the firmware to the latest version before raising the issue in the [RetroPie Forums](https://retropie.org.uk/forum).
* Try choosing a different 'mode' when pairing a 8BitDo controller if the controller doesn't work in EmulationStation. Most controllers allow starting with a differnt mode:
   - X-Input mode (recommended) by pressing _Start_ and _X_ buttons
   - D-Input mode by pressing _Start_ and _B_
   - Nintendo Switch mode by pressing _Start_ and _Y_
   - macOS mode by pressing _Start_ and _A_.

  The start-up button combination may vary by controller, so consult the manual from the support site to get the connect options available for your controller.

## External Links

* <http://support.8BitDo.com> - the 8BitDo support site.
* <https://github.com/libretro/retroarch-joypad-autoconfig/tree/master/udev> - RetroArch configuration profiles for various 8BitDo controllers.
* <https://ladis.cloud/blog/posts/firmware-update-8bitdo.html> - updating the firmware using _fwupdtool/fwupdmgr_.
