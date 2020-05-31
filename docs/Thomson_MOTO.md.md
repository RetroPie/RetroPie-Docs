# Thomson MO/TO

<img src="https://raw.githubusercontent.com/RetroPie/es-theme-carbon/master/moto/art/system.svg" width="400" alt="Thomson MO/TO Logo" title="Thomson MO/TO logo">

[Thomson MO/TO](https://en.wikipedia.org/wiki/Thomson_computers) is a family of 8-bit home computers produced by French company Thomson SA between 1982 and 1989.

| Emulator | Rom Folder | Extension | BIOS |
| :---: | :---: | :---: | :---: |
| [lr-theodore](https://github.com/Zlika/theodore) | moto | .fd .sap .k7 .m5 .m7 .rom | - |

## Emulator: [lr-theodore](https://github.com/Zlika/theodore)

**lr-theodore** is alibretro core for emulation of Thomson computers. It is based on Daniel Coulom's [DCTO8D](http://dcto8.free.fr/), [DCTO9P](http://dcto9p.free.fr/) and [DCMO5](http://dcmo5.free.fr/) emulators, and supports the following models: TO7, TO7/70, TO8, TO8D, TO9, TO9+, MO5, MO6 and also the [Olivetti Prodest PC128](https://it.wikipedia.org/wiki/Olivetti_Prodest_PC_128) (a rebranded MO6 for the Italian market).

## ROMS

Accepted File Extensions:** .fd** and **.sap** (floppy disks),** .k7** (tapes),** .m5/.m7** and **.rom** (cartridges).

Place your MO/TO roms in
```
/home/pi/RetroPie/roms/moto
```

## BIOS
No BIOS file/rom is necessary.

## Controls

`lr-theodore` uses the standard Retroarch input configuration, with the addition of a virtual keyboard when a keyboard is not present.

### Gamepad

| Button | Action |
| :---: | :---: |
| B | _Fire_ button |
| Start | _Start Program_</sup>

_Start Program_ simulates one or several keystrokes on the keyboard to start a game. This feature allows to start most games without the need for a keyboard. The key depends on the loaded media and of the current computer emulated.

| Media loaded | Thomson computer | Key                 |
| ------------: | ---------------- | ------------------- |
| **Floppy disk**  | TO8/TO8D/TO9+    | `B` key (BASIC 512) |
|              | TO9              | `D` key (BASIC 128) |
|              | MO5              | `RUN` + `Enter`        |
| **Tape**         | TO8/TO8D/TO9+    | `C`key (BASIC 1.0) |
|              | TO9              | `E` key (BASIC 1.0) |
|              | MO5/MO6/TO7      | `RUN` or `LOADM"",,R` + `Enter` |
| **Cartridge**    | All but MO5/TO7  | `0` key             |
|              | TO7/TO7-70       | `1` key             |
|              | MO5              | Nothing (cartridges are already autostarted on MO5)


### Keyboard

**Virtual keyboard** Use the `Select` button to show/hide the virtual keyboard. The transparency level of the virtual keyboard can be set in the core's options.

When the virtual keyboard is displayed, the following buttons on the gamepad can be used:

| RetroPad Button | Action | 
| ------------: | :---------------- |
| `Right/Left/Up/Down` | Change focused key on the keyboard |
| `B` | Press the focused key |
| `B` (long press) | Make the key "sticky" (or release it if it was already sticky).<br>Up to 3 keys can be made sticky.<br>All sticky keys are released when the virtual keyboard is hidden.|
|`Start` | Shortcut to press the "Enter" key |
| `Y` | Move the keyboard in the upper or lower part of the screen |

Mapping of the special MO/TO keys to a PC keyboard

| Thomson keyboard | PC keyboard |
| ------------- | ------------- |
| STOP  | TAB  |
| CNT  | CTRL  |
| CAPSLOCK  | CAPSLOCK  |
| ACC  | BACKSPACE  |
| HOME  | HOME  |
| Arrows  | Arrows  |
| INS  | INSERT  |
| EFF  | DEL  |
| RAZ  | ALT  |
| F1-F5  | F1-F5  |
| F6-F10  | SHIFT+F1-F5  |
| Yellow key (MO5) | Left SHIFT |
| BASIC (MO5/MO6) | Right SHIFT |


### Lightpen

The computer's light pen inputs are mapped to the mouse inputs.
