From http://blog.petrockblock.com/2012/07/22/retropie-setup-an-initialization-script-for-retroarch-on-the-raspberry-pi/#comment-818063235:

> I found out that after the selection of a game, the control goes over to the second controller! This seems to be somehow a speciality of the All-Stars ROM. But at least, it is playable :-)

Alternatively if you only have one controller (or play alone) you can do the following:

From http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=79083

> I managed to figure out a fix so the controls work in Super Mario All-Stars and also doesn't break other games (Mario Kart, Super Bomberman etc). This problem has been bugging me for ages and I had to figure out a way to play this game for nostalgia sake. This fix will unfortunately mean player two controls wont work for other games (but I play alone anyway and this is for people with one controller). Simply post this in your blank retroarch.cfg in the snes folder. P.S Remember to change the button numbers/axis for you own controller.

input_player1_joypad_index = "0"
input_player1_b_btn = "2"
input_player1_y_btn = "3"
input_player1_select_btn = "8"
input_player1_start_btn = "9"
input_player1_up_axis = "-1"
input_player1_down_axis = "+1"
input_player1_left_axis = "-0"
input_player1_right_axis = "+0"
input_player1_a_btn = "1"
input_player1_x_btn = "0"
input_player1_l_btn = "4"
input_player1_r_btn = "5"
input_enable_hotkey_btn = "8"
input_exit_emulator_btn = "9"

input_player2_joypad_index = "nul"
input_player2_b_btn = "nul"
input_player2_y_btn = "nul"
input_player2_select_btn = "nul"
input_player2_start_btn = "nul"
input_player2_up_axis = "nul"
input_player2_down_axis = "nul"
input_player2_left_axis = "nul"
input_player2_right_axis = "nul"
input_player2_a_btn = "nul"
input_player2_x_btn = "nul"
input_player2_l_btn = "nul"
input_player2_r_btn = "nul"
input_enable_hotkey_btn = "nul"
input_exit_emulator_btn = "nul"

input_player1_a = "nul"
input_player1_b = "nul"
input_player1_y = "nul"
input_player1_x = "nul"
input_player1_start = "nul"
input_player1_select = "nul"
input_player1_l = "nul"
input_player1_r = "nul"
input_player1_left = "nul"
input_player1_right = "nul"
input_player1_up = "nul"
input_player1_down = "nul"
input_exit_emulator = "nul"

input_player2_a = "nul"
input_player2_b = "nul"
input_player2_y = "nul"
input_player2_x = "nul"
input_player2_start = "nul"
input_player2_select = "nul"
input_player2_l = "nul"
input_player2_r = "nul"
input_player2_left = "nul"
input_player2_right = "nul"
input_player2_up = "nul"
input_player2_down = "nul"
input_exit_emulator = "nul"