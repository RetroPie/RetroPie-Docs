
***

![samcoupe](https://cloud.githubusercontent.com/assets/10035308/14407343/6f8941b2-fe82-11e5-9c8a-df7d53f396c6.jpg)

***
_The SAM Coupé was an 8 bit computer released in 1989._

***

### Emulator: [SimCoupe](http://www.simcoupe.org/) (EXPERIMENTAL!)

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [SimCoupe](http://www.simcoupe.org/) | samcoupe  | .dsk .mgt .sbt .sad | none | keyboard /opt/retropie/configs/simcoupe/SimCoupe.cfg |

### ROMS

Accepted File Extensions: **.dsk .mgt .sbt .sad**

Place your SAM Coupé ROMs in:

```
/home/pi/RetroPie/roms/samcoupe
```

### Controls:

```
KEYBOARD INPUT

The default SAM keyboard mode allows letters, digits and symbols to be typed
as normal on your keyboard, with SimCoupe automatically converting them to the
appropriate SAM key sequence. There's also a Spectrum mapping mode to use when
running Spectrum software, and a raw mode to disable the mappings.

The SAM has a keypad of function keys from F0 to F9 located on the right-side
of the keyboard. For similar key positions in SimCoupe, the SAM keypad is
mapped to the numeric keypad on your keyboard. You'll need to have Numlock
enabled for these keys to be recognised. Don't forget that when SAM software
refers to function keys, you must use the numeric keypad instead!

F1 to F12 keys on your keyboard are used for emulator functions, with the
default mappings shown below. Under OS X, keys F9 to F12 are used by Expose
and Dashboard, so you'll need to hold the Command key in addition to the
combinations below to access them.

             F1 = Open disk 1
       Shift-F1 = Eject disk 1
        Ctrl-F1 = Save disk 1
         Alt-F1 = New disk 1
             F2 = Open disk 2
       Shift-F2 = Eject disk 2
        Ctrl-F2 = Save disk 2
         Alt-F2 = New disk 2
             F3 = Tape browser
             F4 = Import data
       Shift-F4 = Export data
         Alt-F4 = Exit application
             F5 = Toggle 5:4 display
             F6 = Toggle display smoothing
             F7 = Toggle CRT scanlines
       Shift-F7 = Toggle hi-res scanlines
             F8 = Toggle full-screen
             F9 = Debugger
       Shift-F9 = Save screenshot
            F10 = Options
            F11 = NMI Button
            F12 = Reset button
       Ctrl-F12 = Exit application

      PrintScrn = Save SAM screenshot in PNG format
          Pause = Pause emulation
    Scroll Lock = Pause emulation
     Ctrl-Break = Reset
  Ctrl-Keypad * = Reset
  Ctrl-Keypad - = Normal emulation speed
       Keypad - = Reduce emulation speed
       Keypad + = Increase emulation speed
       Keypad * = Turbo speed

Turbo speed disables the frame sync and sound, and limits the display to just
5 frames per second. This usually gives a big speed boost, which is useful for
zooming through slow sections in games and demos, etc.


SAM shift modifier keys and special symbols are mapped as follows:

         Insert = Inv
      Left-Ctrl = Symbol
     Right-Ctrl = Cntrl
       Left-Alt = Cntrl (if enabled)
      Right-Alt = Edit  (if enabled)
       Menu Key = Edit
  ` (backtick)  = (c)
  . (on keypad) = (c)
    § (section) = #

The following additional combinations are also provided for convenience, since
they map common keys to the equivalent function on the SAM:

     Native key   SAM key
     ----------   -------
         Delete = Shift-Delete
        Numlock = Symbol-Edit  (toggles SAM BASIC keypad mode)
           Home = Cntrl-Left
            End = Cntrl-Right
        Page Up = F4
      Page Down = F1


* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
```