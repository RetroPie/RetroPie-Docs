***
![neogeo](https://cloud.githubusercontent.com/assets/10035308/12213399/9cd6b3c0-b634-11e5-9279-97d936f8028c.png)
***
_The Neo Geo is a cartridge-based arcade system board and home video game console released by SNK in 1990._
***

| Emulator | Rom Folder | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: |
| [lr-fba-next](https://github.com/libretro/libretro-fba) | arcade **or** fba **or** neogeo  | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [lr-fba](https://github.com/libretro/fba-libretro) | arcade **or** fba **or** neogeo  | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [PiFBA](https://github.com/RetroPie/pifba) | arcade **or** fba **or** neogeo  | neogeo.zip | /opt/retropie/emulators/pifba/fba2x.cfg **or** /opt/retropie/configs/fba/fba2x.cfg |
| [GnGeo-Pi](https://github.com/ymartel06/GnGeo-Pi) | arcade **or** neogeo | neogeo.zip | /opt/retropie/configs/neogeo/gngeorc |

## Emulators: [GnGeo-Pi](https://github.com/ymartel06/GnGeo-Pi), [PiFBA](https://github.com/RetroPie/pifba), [lr-fba](https://github.com/libretro/fba-libretro), [lr-fba-next](https://github.com/libretro/libretro-fba)

For Neo Geo games you can use either the standalone emulators PiFBA and GnGeo-Pi or the Retroarch core FBA-libretro. lr-fba is recommended because you can use shaders. See [this page.](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha) 

## ROMS

Accepted File Extension: **.zip**

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

Place your Neo Geo ROMs in
```
/home/pi/RetroPie/roms/neogeo
```

#### Gngeo-pi

As a lovely caveat if you're using gngeopi, the ROMs you have must match the file in gngeo_data.zip located at:
```
/opt/retropie/emulators/gngeopi/share/gngeo
```
You can only play roms that have the same name as these .drv files, e.g. mslug2.zip (rom) and mslug2.drv (data). If the names of these files dont match the game will crash. (see the list below for compatible Roms)

GnGeo-Pi based on **0.138** romsets (May 2010)

Total Games Emulated: 203

[**GnGeo-Pi COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1A_a_9t14uzDUMrrO0RgLDwiVUiycmclcPIs6cU6Iox8/edit?usp=sharing)  feel free to contribute to the list.

## BIOS
Neo Geo requires a **neogeo.zip** BIOS file. It will be placed with your ROMs in
```
/home/pi/RetroPie/roms/neogeo
```

These are the contents of a verified working neogeo.zip BIOS file * Note that all the files may not be necessary
```shell
000-lo.lo
asia-s3.rom
filelist.txt
japan-j3.bin
neo-geo.rom
ng-lo.rom
ng-sfix.rom
ng-sm1.rom
sfix.sfix
sm1.sm1
sp-1v1_3db8c.bin
sp-45.sp1
sp-e.sp1
sp-j2.sp1
sp-s.sp1
sp-s2.sp1
sp-u2.sp1
sp1.jipan.1024
uni-bios_1_0.rom
uni-bios_1_1.rom
uni-bios_1_2.rom
uni-bios_1_2o.rom
uni-bios_1_3.rom
uni-bios_2_0.rom
uni-bios_2_1.rom
uni-bios_2_2.rom
uni-bios_2_3.rom
uni-bios_2_3o.rom
uni-bios_3_0.rom
uni-bios_3_1.rom
vs-bios.rom
```
## How to save BIOS settings

The first thing you need to do is go into the Retroarch GUI/Menu and go to “Options” and then go to “Core Options”. Make sure the “Neo Game Mode” is set to “Unibios”. 

After that, if you load a Neo Geo game such as Metal Slug, you can hit the Neo Geo buttons A + B + C during the rom boot up to access the full UniBios menu. Here you can change the game region to whatever you want, and can also change it from MVS (arcade) to AES (console). Any changes made here will be saved until your change them again. After you do that, exit out of the game via “Quit RetroArch” and then reload the rom.

During the second rom boot up, hit the Neo Geo buttons B + C + D this time to bring up the Test Mode screen. Here you can change all of the gameplay settings such as difficulty and add blood. When you save this, it again will be there even after a full system reboot so you can edit to your liking and not have to do it again.

## Controls

### lr-fba and lr-fba-next

lr-fba and lr-fba-next utilise RetroArch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) 

![neogeodiagram](https://cloud.githubusercontent.com/assets/10035308/8245309/a575cc8c-15e9-11e5-8735-0a4ab2a4e137.png)

### GnGeo-Pi Controls
Once you've started GnGeo-Pi at least once a file called gngeorc will be created here
```
/home/pi/.gngeo/gngeorc
```
**Example Configurations**

```shell
 Xbox360
 p1control A=J0B0,B=J0B1,C=J0B2,D=J0B3,START=J0B6,COIN=J0B10,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0,MENU=J0B7
 Dualshock2
 p1control A=J0B2,B=J0B1,C=J0B3,D=J0B0,START=J0B9,COIN=J0B8,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0

 Meaning of the code:
 Kxxx : keyboad key number xxx
 JxByy : Joystick number x Button
 JxAyy : Joystick number x Axe yy (use a lowercase 'a' if you need to invert the axis)
 JxHyy : Joystick number x Hat yy

 by the way, you can define a button multiple time, for example A=J0B0,A=K123,etc..
```

### PiFBA Controls

PiFBA controls are located in
```shell
/opt/retropie/emulators/pifba/fba2x.cfg
```
As there is no menu to configure controllers with PiFBA like there is with Mame4all, you'll have to edit the aforementioned file manually.

**Example of fba2x.cfg**

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

## List of ROMS (for GnGeo-Pi)

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