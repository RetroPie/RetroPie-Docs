![Atari ST](http://www.z80.eu/images/atarilogo.jpg)
***
_The Atari ST, STE, TT, and Falcon were a series of personal computers released by Atari starting in 1985._
***
## Emulator: [Hatari](http://hatari.tuxfamily.org/)
Much of the emulation for later models, such as the Falcon, is still experimental so some games may be hit and miss.

## es_systems.cfg
```
<system>
    <name>atariststefalcon</name>
    <fullname>Atari ST, STE, Falcon</fullname>
    <path>~/.emulationstation/roms/atariststefalcon</path>
    <extension>.st, .stx, .img, .rom</extension>
    <command>%HOMEPATH%\.emulationstation\systems\retroarch\retroarch.exe -L %HOMEPATH%\.emulationstation\systems\retroarch\cores\hatari_libretro.dll "%ROM_RAW%"</command>
    <platform>atariststefalcon</platform> 
    <theme>atariststefalcon</theme>
  </system>
```

## ROMS
Accepted File Extensions: **.st, .stx, .img, .rom**

Place your Atari ST/STE/TT/Falcon ROMS in
```shell
.emulationstation\roms\atariststefalcon
```