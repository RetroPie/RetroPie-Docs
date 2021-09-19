***
![neogeo](https://cloud.githubusercontent.com/assets/10035308/12213399/9cd6b3c0-b634-11e5-9279-97d936f8028c.png)
***
_The Neo Geo is a cartridge-based arcade system board and home video game console released by SNK in 1990._

See also: [FinalBurn Neo](FinalBurn-Neo), [MAME](MAME).
***
There are a variety of arcade emulators available in RetroPie which can emulate Neo Geo games. There are significant differences in performance, compatibility, and configuration between them. If you're getting started with arcade emulation, start by reading [Arcade](Arcade).

This page is a resource for additional details on configuring a dedicated set of Neo Geo ROMs including configuration paths, controls, and the ROM sets which each emulator requires.
***

| Emulator | Rom Folder | Extension | Required ROM Version | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fbneo](https://github.com/libretro/fbneo) | neogeo  | .7z .zip | FB Neo v1.0.0.1 | /opt/retropie/configs/neogeo/retroarch.cfg |
| [lr-fbalpha2012](https://github.com/libretro/fbalpha2012) | neogeo  | .7z .zip | FB Alpha v0.2.97.30 | /opt/retropie/configs/neogeo/retroarch.cfg |
| [PiFBA](https://github.com/RetroPie/pifba) | neogeo  | .zip | FB Alpha 0.2.96.71 | /opt/retropie/emulators/pifba/fba2x.cfg |
| [GnGeo-Pi](https://github.com/ymartel06/GnGeo-Pi) | neogeo | .zip | MAME 0.138 | /opt/retropie/configs/neogeo/gngeorc |

## Emulators: [lr-fbneo](lr-fbneo), [lr-fbalpha2012](FinalBurn-Neo#lr-fbalpha2012), [PiFBA](FinalBurn-Neo#pifba), [GnGeo-Pi](Neo-Geo#gngeo-pi)
Refer to the main [FinalBurn Neo](FinalBurn-Neo) page for general information on all FinalBurn emulators or the direct links above for in-depth infomation on `lr-fbneo`, `lr-fbalpha2012`, or `PiFBA`. In-depth information on `GnGeo-Pi` can be found below.

*lr-fbneo* is the prefered Pi 2 (and later) Neo Geo emulator due to its accuracy. 

*lr-fbalpha2012* is useful for any games that may be running slow in the latest version of lr-fbneo for a Pi 3/Pi 2, and if used exclusively instead of `lr-fbneo` will allow you to do full system updates without worrying about needing to update your ROM Set, but comes at the cost of inaccuracy such as games having audio issues across the entire library and other issues that have been fixed in the latest version of `lr-fbneo`.

*PiFBA* is recommended for those on a Pi 0 or Pi 1.

## ROMS
Accepted File Extensions: **.7z .zip**

Place Neo Geo ROMs in:
```
/home/pi/RetroPie/roms/neogeo
```
## BIOS

Neo Geo ROMs require a `neogeo.zip` BIOS file with the exact same MAME or FB Neo version as the emulator you select. If you're using `lr-fbneo` or `lr-fbneo-2012`, you can copy the BIOS file in:
```
/home/pi/RetroPie/BIOS/fbneo
```
For other emulators, you can copy the BIOS file in the same folder as the ROMS:
```
/home/pi/RetroPie/roms/neogeo
```

Instructions on how to install the Neo Geo Unibios on lr-fbneo can be found here: [lr-fbneo Neo Geo Bios](lr-fbneo#neo-geo-unibios). The Unibios can be used as documented on the official page at <http://unibios.free.fr/howitworks.html>.

* On the Unibios boot screen
  * Neo Geo **A+B+C** (RetroPad B+A+Y) for BIOS Menu
  * Neo Geo **B+C+D** (RetroPad A+Y+X) for Test Menu
* At any time
  * Neo Geo **Start+A+B+C** (RetroPad Start+B+A+Y) for In-Game Menu

The menus allow you to change various settings like region, dip switch settings for gameplay options like difficulty or blood, and coin or free play settings. Unibios settings will persist after quitting FBA, launching another Neo Geo game, or rebooting RetroPie.

## Controls
You will configure controls differently depending on which emulator you use:
### lr-fbneo and lr-fbalpha2012

lr-fbneo and lr-fbalpha2012 utilise RetroArch configs. Add custom RetroArch controls to the `retroarch.cfg` file in:
```
/opt/retropie/configs/neogeo/retroarch.cfg
```

For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration) 

---

### PiFBA

PiFBA controls are located in:
```
/opt/retropie/emulators/pifba/fba2x.cfg
```

As there is no menu to configure controllers with PiFBA, like there is with Mame4all, you'll have to edit the aforementioned file manually.

**Example fba2x.cfg**:
```shell
[Keyboard]
# Get codes from /usr/include/SDL/SDL_keysym.h
A_1=306 #LCTRL (button1)
B_1=32 #SPACE (button3)
X_1=308 #LALT (button2
Y_1=304 #LSHIFT
L_1=122 #z
R_1=120 #x
START_1=49 #1
SELECT_1=53 #5
LEFT_1=276 #left
RIGHT_1=275 #right
UP_1=273 #up
DOWN_1=274 #down
QUIT=27 #escape
#player 2 keyboard controls, disabled by default
A_2=97 #a (button1)
B_2=113 #q (button3)
X_2=115 #s (button2)
Y_2=119 #w
L_2=105 #i
R_2=107 #k
START_2=50 #2
SELECT_2=54 #6
LEFT_2=100 #d
RIGHT_2=103 #g
UP_2=114 #r
DOWN_2=102 #f

[Joystick]
# Get codes from "jstest /dev/input/js0"
# from package "joystick"
A_1=3
B_1=1
X_1=2
Y_1=0
L_1=4
R_1=5
START_1=9
SELECT_1=8
#Joystick axis
JA_LR=0
JA_UD=1
#player 2 button configuration
A_2=3
B_2=1
X_2=2
Y_2=0
L_2=4
R_2=5
START_2=9
SELECT_2=8
#Joystick axis
JA_LR=0
JA_UD=1


[Graphics]
DisplaySmoothStretch=1
# Display Effect: 0 none, 1 scanlines
DisplayEffect=0
DisplayBorder=0
MaintainAspectRatio=1

[Sound]
```

---
### GnGeo-Pi
[Visit the GnGeo-Pi homepage on github](https://github.com/ymartel06/GnGeo-Pi)
```
Roms Dir: /home/pi/RetroPie/roms/neogeo
Binary Dir: /opt/retropie/emulators/gngeopi/bin
Config Dir: /opt/retropie/configs/neogeo
```
**MAME Version**: 0.138 (May 2010)    
**Romsets emulated: 203**    
**GnGeo-Pi DAT File**: [pandora_gngeo_084_dat.zip](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/gngeopi/pandora_gngeo_084_dat.xml)    
**GnGeo-Pi Filtered DAT File**: [pandora_gngeo_084_filtered.zip](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/gngeopi/pandora_gngeo_084_filtered.dat) All clones non-working\mahjong\quiz removed    
**Romsets emulated**: 128

As a caveat, if you're using _gngeo-pi__, the ROMs you have must match the file in `gngeo_data.zip` located at:
```
/opt/retropie/emulators/gngeopi/share/gngeo
```
You can only play roms that have the same name as these `.drv` files, e.g. `mslug2.zip` (rom) and `mslug2.drv` (data). If the names of these files don't match, GnGeo-Pi will crash. (see the list at the bottom of this page for compatible ROMs)

**GnGeo-Pi Controls**

Once you've started GnGeo-Pi at least once a file called `gngeorc` will be created in:
```
/home/pi/.gngeo/gngeorc
```

**Example Configuration:**

```
 Xbox360
 p1control A=J0B0,B=J0B1,C=J0B2,D=J0B3,START=J0B6,COIN=J0B10,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0,MENU=J0B7
 Dualshock2
 p1control A=J0B2,B=J0B1,C=J0B3,D=J0B0,START=J0B9,COIN=J0B8,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0

 Meaning of the code:
 Kxxx : keyboad key number xxx
 JxByy : Joystick number x Button
 JxAyy : Joystick number x Axe yy (use a lowercase 'a' if you need to invert the axis)
 JxHyy : Joystick number x Hat yy

 you can define a button multiple time, for example A=J0B0,A=K123,etc..
```

**List of GnGeo-Pi ROMS**:
```shell
2020bb.drv
2020bba.drv
2020bbh.drv
3countb.drv
alpham2.drv
androdun.drv
aodk.drv
aof.drv
aof2.drv
aof2a.drv
aof3.drv
aof3k.drv
bakatono.drv
bangbead.drv
bjourney.drv
blazstar.drv
breakers.drv
breakrev.drv
bstars.drv
bstars2.drv
burningf.drv
burningfh.drv
cmc42.xor
cmc50.xor
crsword.drv
ct2k3sa.drv
ct2k3sp.drv
cthd2003.drv
ctomaday.drv
cyberlip.drv
diggerma.drv
doubledr.drv
eightman.drv
fatfursa.drv
fatfursp.drv
fatfury1.drv
fatfury2.drv
fatfury3.drv
fbfrenzy.drv
fightfev.drv
fightfeva.drv
flipshot.drv
fswords.drv
galaxyfg.drv
ganryu.drv
garou.drv
garoubl.drv
garouo.drv
garoup.drv
ghostlop.drv
goalx3.drv
gowcaizr.drv
gpilots.drv
gpilotsh.drv
gururin.drv
irrmaze.drv
janshin.drv
jockeygp.drv
joyjoy.drv
kabukikl.drv
karnovr.drv
kf10thep.drv
kf2k2mp.drv
kf2k2mp2.drv
kf2k2pla.drv
kf2k2pls.drv
kf2k3bl.drv
kf2k3bla.drv
kf2k3pcb.drv
kf2k3pl.drv
kf2k3upl.drv
kf2k5uni.drv
kizuna.drv
kof10th.drv
kof2000.drv
kof2000n.drv
kof2001.drv
kof2001h.drv
kof2002.drv
kof2002b.drv
kof2003.drv
kof2003h.drv
kof2k4se.drv
kof94.drv
kof95.drv
kof95h.drv
kof96.drv
kof96h.drv
kof97.drv
kof97a.drv
kof97pls.drv
kof98.drv
kof98k.drv
kof98n.drv
kof99.drv
kof99a.drv
kof99e.drv
kof99n.drv
kof99p.drv
kog.drv
kotm.drv
kotm2.drv
kotmh.drv
lans2004.drv
lastblad.drv
lastbladh.drv
lastbld2.drv
lastsold.drv
lbowling.drv
legendos.drv
list.txt
lresort.drv
magdrop2.drv
magdrop3.drv
maglord.drv
maglordh.drv
mahretsu.drv
marukodq.drv
matrim.drv
matrimbl.drv
miexchng.drv
minasan.drv
mosyougi.drv
ms4plus.drv
ms5pcb.drv
ms5plus.drv
mslug.drv
mslug2.drv
mslug3.drv
mslug3b6.drv
mslug3h.drv
mslug3n.drv
mslug4.drv
mslug5.drv
mslug5h.drv
mslugx.drv
mutnat.drv
nam1975.drv
ncombat.drv
ncombath.drv
ncommand.drv
neobombe.drv
neocup98.drv
neodrift.drv
neogeo.drv
neomrdo.drv
ninjamas.drv
nitd.drv
nitdbl.drv
overtop.drv
panicbom.drv
pbobbl2n.drv
pbobblen.drv
pbobblena.drv
pgoal.drv
pnyaa.drv
popbounc.drv
preisle2.drv
pspikes2.drv
pulstar.drv
puzzldpr.drv
puzzledp.drv
quizdai2.drv
quizdais.drv
quizkof.drv
ragnagrd.drv
rbff1.drv
rbff1a.drv
rbff2.drv
rbff2h.drv
rbff2k.drv
rbffspec.drv
ridhero.drv
ridheroh.drv
roboarmy.drv
rotd.drv
s1945p.drv
samsh5sp.drv
samsh5sph.drv
samsh5spn.drv
samsho.drv
samsho2.drv
samsho3.drv
samsho3h.drv
samsho4.drv
samsho5.drv
samsho5b.drv
samsho5h.drv
samshoh.drv
savagere.drv
sdodgeb.drv
sengokh.drv
sengoku.drv
sengoku2.drv
sengoku3.drv
shocktr2.drv
shocktra.drv
shocktro.drv
socbrawl.drv
socbrawla.drv
sonicwi2.drv
sonicwi3.drv
spinmast.drv
ssideki.drv
ssideki2.drv
ssideki3.drv
ssideki4.drv
stakwin.drv
stakwin2.drv
strhoop.drv
superspy.drv
svc.drv
svcboot.drv
svcpcb.drv
svcpcba.drv
svcplus.drv
svcplusa.drv
svcsplus.drv
tophuntr.drv
tophuntra.drv
tpgolf.drv
trally.drv
turfmast.drv
twinspri.drv
tws96.drv
viewpoin.drv
vliner.drv
vlinero.drv
wakuwak7.drv
wh1.drv
wh1h.drv
wh1ha.drv
wh2.drv
wh2j.drv
wh2jh.drv
whp.drv
wjammers.drv
zedblade.drv
zintrckb.drv
zupapa.drv
```
