***
DICE is a Discrete Integrated Circuit Emulator. It emulates computer systems that lack any type of CPU, consisting only of discrete logic components.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-dice](https://github.com/mittonk/dice-libretro) | dice | .zip | | |

## Emulator: [lr-dice](https://github.com/mittonk/dice-libretro)
DICE is a Discrete Integrated Circuit Emulator. It emulates computer systems
that lack any type of CPU, consisting only of discrete logic components.

dice-libretro (lr-dice) is a Libretro port of DICE, to run in RetroArch.
 
Pi4 is a reasonable minimum requirement.

Some games (like pong) will run on a
Zero2w, others (like pinpong) will run out of memory.


## ROMS
Accepted File Extensions: **.zip, .dmy**

Some games (pong, breakout, pinpong, etc) do not have any ROM on the board at
all. For these, copy the dummy launcher file from dummy_files to your ROM folder;
these have a correct name (for example, pong.dmy) that will get RetroArch to set
up lr-dice for the correct game.


Place your arcade ROMS in:
```shell
/home/pi/RetroPie/roms/dice
```


## Controls

| Arcade input | Gamepad/Keyboard |
| :- | :- |
| P1 Start | KEY_1,JOY1_BUTTON9  |
| P2 Start | KEY_2,JOY2_BUTTON9  |
| P1 Coin  | KEY_3,JOY1_BUTTON10 |
| P2 Coin  | KEY_4,JOY2_BUTTON10 |
| Service A | KEY_5  |
| Service B | KEY_7  |
| Test A  | KEY_6 |
| Test B  | KEY_8 |
| P1 Joystick Up    | KEY_UP,JOY1_UP       |
| P1 Joystick Down  | KEY_DOWN,JOY1_DOWN   |
| P1 Joystick Left  | KEY_LEFT,JOY1_LEFT   |
| P1 Joystick Right | KEY_RIGHT,JOY1_RIGHT |
| P2 Joystick Up    | JOY2_UP    |
| P2 Joystick Down  | JOY2_DOWN  |
| P2 Joystick Left  | JOY2_LEFT  |
| P2 Joystick Right | JOY2_RIGHT |
