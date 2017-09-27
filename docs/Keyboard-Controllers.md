Using a keyboard as a controller for emulation can be very easy, or it can be challenging and complex depending on your specific hardware and design needs. In principle, a keyboard should be the simplest, most traditional interface to understand, but in practice, a keyboard is rarely used as an _actual keyboard_ when playing games. Usually, a keyboard interface is wired to arcade buttons which introduces another layer of abstraction to your configuration and additional considerations when you are trying to troubleshoot controls.

### Why bother with a keyboard?
In the early days of arcade emulation, MAME was running on computers which, naturally, have keyboards. In order to emulate the movements of a joystick, pushbuttons, coin insert, etc., specific keys on the computer's keyboard were used. As more arcade hardware was emulated, systems often had similar controls. A standard set of keyboard keys was quickly established to serve as the typical inputs to common hardware controls (Insert Coin, Start, Up, Down, Left, Right, etc.).

Before long, some enterprising individuals realized that they could pop open their computer keyboard to gain access to the circuit board and solder wires to the key switches. They could run the wires to actual arcade parts (joystick switches and pushbuttons) which were available from manufacturers for servicing actual arcade systems. It was possible to build an arcade cabinet from scratch using _real_ arcade controls and wire them to a computer keyboard and play emulated games.

Hacking an actual keyboard is still done today, but going this route can lead to problems. Functionality when typing is not the same as the requirements for multi-player gaming. Hacking inexpensive keyboards in order to build arcade controls can reveal issues like ghosting (problems when pressing too many buttons simultaneously), or interaction delays that you might not notice when typing but that will ruin a gaming experience. A popular solution is to use a dedicated keyboard controller designed for arcade emulation. These devices are built to overcome the problems with hacking actual keyboards.

## Types of Keyboard Interfaces
### USB Keyboard
The most basic example of a keyboard interface is just a regular PC USB keyboard which can be used as-is. If you were only planning to emulate a computer--like maybe an Apple II for example--this would be sufficient. At minimum, you would want to hold down a key after the first boot into Emulation Station in order to setup navigation capabilities (arrows for up, down, etc.). Of course, as described above, a regular keyboard can also be hacked and wired to arcade controls, but there are better solutions:
### USB Keyboard Controller Board
Dedicated controllers like the Ultimarc IPAC series and similar USB interfaces are essentially robust keyboards without keys. Instead, they have screw-down terminals, header pins or solder pads to which you wire your own buttons. The terminals typically have labels for the buttons/switches and player numbers that should be connected (Coin, Start, UP, DOWN, LEFT, etc.). These often correspond the common key-mapping scheme used in MAME. Triggering a pushbutton actually just sends a particular keystroke to the computer. Note that some boards have a _gamepad mode_ (or firmware) instead of a keyboard mode. In such cases, the board is not acting like a keyboard, but rather a gamepad/joystick.
### GPIO (virtual) Keyboard Driver
It is possible to wire buttons directly to GPIO pins and then run a software driver that translates the input from the pins into keyboard keystrokes. This is like using a controller board above _without the board_. On the Raspberry Pi, software such as Adafruit-Retrogame or GPIOnext are good examples of virtual keyboard drivers. These drivers are limited by the available GPIO pins.

## Configuration Example: IPAC
We can follow the example of setting up an Ultimarc IPAC controller as a model for other keyboard controllers which may follow similar steps, but here are some specific details about the popular IPAC controller from Ultimarc.
### IPAC Features
It is important to understand that the IPAC is a highly capable board with several features that can cause undue challenges if not fully understood. The IPAC comes in several models to support various configurations and all of the boards can be configured using the WinIPAC utility supplied and supported by Ultimarc.
- **Keybaord Mode vs. Gamepad Mode**: Original IPAC hardware (pre-2015) was only ever capable of running as a keyboard controller. Both "large chip" designs as well as updated versions of IPAC boards that still have a PS/2 connecter can be connected via USB with the appropriate cable and will appear to the computer as a keyboard device. More recent designs coupled with newer firmware allow IPAC boards to appear as a gamepad/joystick to the computer. While this may be desirable for some users, we are focusing on the configuration as a keyboard controller, so it may help to check this using the WinIPAC utility before you start to ensure your IPAC is configured in Keyboard Mode.
- **Key Mapping**: In Keyboard Mode, the IPAC inputs are mapped by default to the keys that correspond to the MAME emulator. For example, Player 1 UP,DOWN,LEFT,RIGHT each map to respective arrow keys, SW1 (button 1) is LEFT_CONTROL, and so on. This is how MAME expects the controls to work. It can be helpful to keep these defaults unless you absolutely know what keys you want to correspond to each button as wired. You can make adjustments to how your controller is mapping its keys (again, using Ultimarc's WinIPAC utility).
- **SHIFT Function**: The IPAC includes a special SHIFT function. This is best explained by reading through Ultimarc's documentation, but SHIFT functionally works like a hotkey. However, it has nothing to do with RetroArch hotkeys and is often a source of confusion for new IPAC owners. This feature can be very useful on stand-alone emulators, but we mention it here now more to point it out than to provide specific guidance. SHIFT functions can also be configured using the WinIPAC utility.

### Keyboard Mode, DEFAULT KEYS
Assuming the an IPAC2 is setup in Keyboard Mode using factory-default keys, you can wire your controller to your pushbuttons and joystick switches following the labels on the board. If done correctly, when you plug the IPAC into a USB port, the computer sees a keyboard, and pressing on your wired buttons will trigger keypresses as follows:
```
Label		Key
------		------
COIN 1		5	
COIN 2		6	
START 1		1	
START 2		2
1 RIGHT		R arrow
1 LEFT		L arrow
1 UP		U arrow
1 DOWN		D arrow
1 SW 1		L-ctrl
1 SW 2		L-alt	
1 SW 3		space	
1 SW 4		L-shift	
1 SW 5		Z	
1 SW 6		X	
1 SW 7		C	
1 SW 8		V	
1 A		P	
1 B		ENTER	
START 1		1	
START 2		2
2 RIGHT		G	
2 LEFT		D	
2 UP		R	
2 DOWN		F	
2 SW 1		A	
2 SW 2		S	
2 SW 3		Q	
2 SW 4		W	
2 SW 5		I	
2 SW 6		K	
2 SW 7		J	
2 SW 8		L	
2 A		TAB	
2 B		ESC
```
### Emulation Station and RetroArch
When you first boot into Emulation Station, it may not detect any gamepads/joysticks, but you can press a wired pushbutton and it will detect the keyboard. Simply proceed through the menu configuring your controls as described in the [First Installation documentation](https://github.com/RetroPie/RetroPie-Setup/wiki/First-Installation#controller-configurations). It is ultimately up to you to decide which of your wired buttons will correspond to the virtual gamepad inputs used by the different emulators. Just be aware of the layers of abstraction. For example, you may be configuring "button A" by pressing a pushbutton wired to IPAC Player1_SW1, which will correspond to LEFT_CONTROL on a keyboard. Logically speaking, you are mapping LEFT_CONTROL to "button A". Understanding how your keyboard interface works, how you have it wired to your buttons, and how pushing buttons actually sends keystrokes and virtual gamepad input can be helpful if you decide to deviate from your initial mapping, for one particular emulator, or for a single ROM configuration.

Here is an example of a possible RetroArch configuration (a section of the `opt/retropie/configs/all/retroarch.cfg`) which can also be manually edited:
```
input_player1_a = alt
input_player1_b = ctrl
input_player1_y = shift
input_player1_x = space
input_player1_start = num1
input_player1_select = num5
input_player1_l = z
input_player1_r = x
input_player1_left = left
input_player1_right = right
input_player1_up = up
input_player1_down = down

input_player2_a = s
input_player2_b = a
input_player2_y = w
input_player2_x = q
input_player2_start = num2
input_player2_select = num6
input_player2_l = i
input_player2_r = k
input_player2_left = d
input_player2_right = g
input_player2_up = r
input_player2_down = f
```
RetroArch's use of these configuration files is [described in detail here](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration) with references to gamepad/joystick controllers. The main difference in the configuration files with respect to keyboard controllers is the lack of `_btn` in the mapping. For example, notice how we have
`input_player1_a = alt`
for a keyboard input instead of
`input_player1_a_btn = 1`
for a gamepad input. Aside from this subtle difference, the other details about how `retroarch.cfg` files work and how it is possible to override settings by system and by ROM still apply.

Note that even though your inputs originate as raw keystrokes, the RetroArch configuration ensures that your keys generate virtual gamepad signals as well. Some emulators require input from the RetroPad gamepad this way while others (like lr-mame2003) will detect both.

### Stand-alone Emulators
Emulators that are not Libretro cores will have their own configurations separate from the config files described above. Whether automatically generated or manually updated, knowing how your buttons map to keystrokes will go a long way toward understanding the layers of abstraction. In some respects, the standalone emulators are easier to understand because they remove the RetroArch layer. 

### MAME GUI (TAB MENU)
In some versions of MAME (lr-mame2003, AdvanceMAME) it may be much easier to make per-ROM tweaks within the MAME GUI menu. Pressing TAB will bring up the menu, and editing controls for THIS GAME can be a fast way to make minor adjustments to better match your button layout to a particular arcade title.

### Conflicts
It is possible to have conflicts with your keyboard controller such that a direction or a pushbutton keystroke is pre-configured as an input for some other function in RetroArch. If you think you have a conflict with some function (turbo mode, for example) you may need to edit your `opt/retropie/configs/all/retroarch.cfg` and find the line that uses your key and change it to something else. You can also set unused functions to `= null` which will remove the conflict (and disable access to the feature).