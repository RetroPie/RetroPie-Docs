After pairing the device as shown in this [guide](https://github.com/retropie/retropie-setup/wiki/Setting-up-a-Bluetooth-controller) and mapping it thorugh emulationstation menú, the first thing you will notice is that it isn't working ingame.

The problem is that the keys detected in emulationstation are not the same as the ones detected in retroarch. To fix this you can either bind the keys through the retroarch config (in emulationstation: Retropie -> Retroarch -> Config -> Input) or start from the following cfg that must be placed at `/opt/retropie/configs/all/retroarch-joypads/udev/小米蓝牙手柄.cfg`. The name is the same as the one in `/opt/retropie/configs/all/retroarch-joypads` that represents the Xiaomi Gamepad.

```
input_device = "小米蓝牙手柄"
input_driver = "udev"
input_r_y_plus_axis = "+5"
input_l3_btn = "17"
input_r_x_minus_axis = "-2"
input_l_btn = "10"
input_load_state_btn = "10"
input_start_btn = "15"
input_exit_emulator_btn = "15"
input_l_y_minus_axis = "-1"
input_up_btn = "h0up"
input_r_y_minus_axis = "-5"
input_a_btn = "4"
input_b_btn = "5"
input_reset_btn = "5"
input_down_btn = "h0down"
input_l_x_plus_axis = "+0"
input_l_y_plus_axis = "+1"
input_r_btn = "11"
input_save_state_btn = "11"
input_r2_btn = "13"
input_r3_btn = "18"
input_right_btn = "h0right"
input_state_slot_increase_btn = "h0right"
input_x_btn = "7"
input_menu_toggle_btn = "7"
input_select_btn = "14"
input_enable_hotkey_btn = "14"
input_l_x_minus_axis = "-0"
input_y_btn = "8"
input_left_btn = "h0left"
input_state_slot_decrease_btn = "h0left"
input_r_x_plus_axis = "+2"
input_l2_btn = "12"
```

Keep in mind that this configuration is based in the Xbox 360 Controller Scheme and uses the default joypad hotkeys