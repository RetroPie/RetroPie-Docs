![Final Burn Alpha Logo](http://i.imgur.com/tXkQiWN.png)
***
_Final Burn Alpha is a Multiple Arcade Emulator most popular for emulating Neo-Geo, Capcom, Konami, and Cave games. It is developed by the final burn team and originated from FinalBurn by Dave_
***
## Emulators: [PiFBA](https://github.com/RetroPie/pifba), [fba-libretro](https://github.com/libretro/fba-libretro), [fba-libretro-next](https://github.com/libretro/libretro-fba.git)

Fba-libretro is a port of PiFBA and unlike PiFBA, fba-libretro uses RetroArch configurations.

## ROMS

Accepted File Extensions: **.zip**

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

### PiFBA 

Romset Used: FBA **0.2.96.71 romset** which is based on MAME 0.114 (April 2007) (see list below) 

Total Games Emulated: 684 (no clones)

### [**PiFBA COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing)  feel free to contribute to the list.

For PiFBA place your ROMS in

```shell
/home/pi/RetroPie/roms/fba
```

you can also place your roms in

```shell
/home/pi/RetroPie/roms/neogeo
```

### FBA-Libretro

Romset Used: FBA **0.2.97.30** which is based on MAME 0.154 (Jul 2014)

Total Games Emulated: 3369 (includes clones etc..)

### [**FBA-Libretro COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing)  feel free to contribute to the list.
 
Place your  FBA-Libretro ROMS in
```shell
/home/pi/RetroPie/roms/fba
```
you can also place your roms in

```shell
/home/pi/RetroPie/roms/neogeo
```

### FBA-Libretro-Next

Romset Used: FBA **0.2.97.36**
 
Place your Fba-libretro-next ROMS in
```shell
/home/pi/RetroPie/roms/fba
```
you can also place your roms in

```shell
/home/pi/RetroPie/roms/neogeo
```
## BIOS

The BIOS needed for Neo Geo games is:

**neogeo.zip**

* Note that unlike other BIOS that go in the BIOS folder, this BIOS will go into the same folder as your ROMS.

For RetroPie 3.0 for PiFBA and FBA-Libretro place your BIOS in
```shell
/home/pi/RetroPie/roms/fba
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

## Controls
As there are 2 emulators there are two sets of controls.
### fba-libretro Controls
fba-libretro utilises RetroArch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) 

![neogeodiagram](https://cloud.githubusercontent.com/assets/10035308/8245309/a575cc8c-15e9-11e5-8735-0a4ab2a4e137.png)

One important thing to note is that with fba-libretro the hotkey button (i.e. select) interferes with you insert coin button (which also happens to be select) so as a result you can't insert a coin to start your game with the default controls. An easy fix is to to swap the hotkey and exit button around in the aforementioned retroarch.cfg.

### PiFBA Controls
PiFBA controls are located in
```shell
/opt/retropie/emulators/pifba/fba2x.cfg
```
As there is no menu to configure controllers with PiFBA like there is with Mame4all, you'll have to edit the aforementioned file manually. 

**NOTE** PiFBA currently only supports 2 players.

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
## Video Tutorial:

<a href="https://www.youtube.com/watch?v=C7ETQUBNVRo" target="_blank"><img src="https://i.ytimg.com/vi_webp/C7ETQUBNVRo/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a>

## List of Hardware Supported
* Capcom CPS-1
* Capcom CPS-2
* Capcom CPS-3
* Cave
* Data East DEC-0, DEC-8 and DECO IC16 based games
* Galaxian based hardware
* Irem M62, M63, M72, M90, M92 and M107 hardware
* Kaneko 16
* Konami
* Neo-Geo
* NMK16
* Pacman based hardware
* PGM
* Psikyo 68EC020 and SH-2 based hardware
* Sega System 1, System 16 (and similar), System 18, X-Board and Y-Board
* Super Kaneko Nova System
* Toaplan 1
* Toaplan 2
* Taito F2, X, Z and others
* Miscellaneous drivers for lots of other hardware

# Complete List of PiFBA Rom Files
```shell
 You have 684 of 684 known FBA 0.2.96.71 OpenDingux working ROMs sets

1941
1941j
1944
1944j
1945kiii
19xx
19xxa
19xxb
19xxh
19xxj
19xxjr1
2020bb
2020bba
2020bbh
3countb
3in1semi
3wonders
3wonderu
4in1boot
aerofgt
afighter
agallet
alexkid1
alexkidd
aliensy1
aliensy2
aliensy3
aliensyn
alpham2
altbeas5
altbeasj
altbeast
androdun
aodk
aof
aof2
aof2a
aof3
area88
armwar
armwara
armwarr1
armwaru
aurail
aurail1
aurailj
avsp
avspa
avsph
avspj
avspu
bakatono
bakubrkr
batcir
batcira
batcirj
bcstry
bcstrya
berlwall
berlwalt
biomtoy
bjourney
blazeon
blazstar
bloodwar
bodyslam
bombjac2
bombjack
bonkadv
breakers
bstars
bstars2
burglarx
burningf
burningh
captcomj
captcomm
captcomu
cawing
cawingj
cawingr1
cawingu
chikij
chokchok
choko
cookbib
cookbib2
cookbib3
crsword
csclub
cscluba
csclubh
csclubj
ctomaday
cworld2j
cyberlip
cybots
cybotsj
cybotsu
daimakai
daisenpu
ddonpach
ddonpchj
ddsom
ddsoma
ddsomb
ddsomj
ddsomjr1
ddsomr1
ddsomr2
ddsomr3
ddsomu
ddsomur1
ddtod
ddtoda
ddtodh
ddtodj
ddtodjr1
ddtodr1
ddtodu
ddtodur1
ddux1
defense
dfeveron
dimahoo
dino
dinoj
dinou
donpachi
donpachk
donpacjp
donpackr
doubledr
dquizgo
drgnbowl
drgw2
drgw2c
dstlk
dstlka
dstlku
dstlkur1
dumpmtmt
dunkshot
dynwar
dynwarj
ecofghta
ecofghtr
ecofghtu
eightman
esprade
espradej
espradeo
explbrkr
fantasia
fantsia2
fantsy95
fantzon1
fantzone
fatfursa
fatfursp
fatfury1
fatfury2
fatfury3
fbfrenzy
feversos
ffight
ffightj
ffightj1
ffightu
ffightua
fightfev
fightfva
finalttr
flipshot
fncywld
fntsia2a
forgottn
fstarfrc
gaia
gaiden
galhustl
galpanic
garou
gensitou
getstarb
ghostlop
ghouls
ghoulsu
gigawing
gmahou
goalx3
goldnax2
goldnaxe
gowcaizr
gpilots
gtmr
gtmr2
gtmr2a
gtmr2u
gtmra
gtmre
gtmrusa
guwange
gwinga
gwingj
hedpanic
hedpanif
hellfir1
hellfir2
hellfire
honeydol
htchctch
hyperpac
hyperpcb
irrmaze
janshin
joyjoy
jumpkids
jumppop
jyangoku
kabukikl
karatblz
karnovr
killbldt
kingdmgp
kizuna
knights
knightsj
knightsu
kod
kodj
kodu
kof2000
kof2001
kof2002
kof2003
kof94
kof95
kof96
kof97
kof98
kof99
kotm
kotm2
kotmh
kov
kov115
kovj
kovplus
kovplusa
lastblad
lastbld2
lbowling
legendos
lostwrld
lresort
magdrop2
magdrop3
maglord
maglordh
mahoudai
mahretsu
marukodq
matrim
mbomberj
mbombrd
mbombrdj
mchampda
mchampdx
megaman
megaman2
megamn2a
mercs
mercsj
mercsu
mercsua
metlsavr
metmqstr
mgcrystj
mgcrystl
mgcrysto
miexchng
minasan
missmw96
missw96
mjleague
mmatrix
mmatrixj
moremore
moremorp
mosyougi
mpang
mpangj
ms5pcb
msh
msha
mshb
mshh
mshj
mshjr1
mshu
mshvsf
mshvsfa
mshvsfa1
mshvsfb
mshvsfb1
mshvsfh
mshvsfj
mshvsfj1
mshvsfj2
mshvsfu
mshvsfu1
mslug
mslug2
mslug3
mslug4
mslug5
mslugx
msword
mswordj
mswordr1
mswordu
mtwins
multchmk
multchmp
mutnat
mvsc
mvsca
mvscar1
mvscb
mvsch
mvscj
mvscjr1
mvscu
nam1975
ncombat
ncombata
ncommand
nemo
nemoj
neobombe
neocup98
neodrift
neogeo
neomrdo
newfant
news
newsa
ninjamas
nmaster
nwarr
nwarrb
nwarrh
nwarru
ohmygod
orld105k
orld111c
orlegend
orlegndc
orlegnde
outzone
outzonea
outzoneb
outzonec
overtop
pang3
pang3j
pangpang
panicbom
pbobbl2n
pbobblen
pbobblna
pfghtj
pgear
pgearr1
pgm
pgoal
photoy2k
plegendj
plegends
pnickj
popbounc
powerina
powerinb
powerins
prehisle
prehislu
preisle2
progear
progeara
progearj
pspikes2
pulstar
punisher
punishrj
punishru
puzlstar
puzzldpr
puzzledp
pwrins2j
pwrinst2
pzloop2
pzloop2j
qad
qadj
qndream
qtono2
quart2
quart21
quizdai2
quizdais
quizkof
raf102j
ragnagrd
raiga
rainbow
rainbowe
rainbowo
rbff1
rbff2
rbffspec
rchase
rckman2j
ridhero
ridheroh
ringdest
riot
riotcity
roboarmy
rockmanj
rotd
ryukenda
ryukendn
s1945p
sailormn
sailormo
samsh5sp
samsho
samsho2
samsho3
samsho4
samsho5
savagere
sdfight
sdi
sdib
sdibl
sdodgeb
semibase
sengokh
sengoku
sengoku2
sengoku3
sf2
sf2accp2
sf2ce
sf2cej
sf2ceua
sf2ceub
sf2ceuc
sf2eb
sf2hf
sf2j
sf2ja
sf2jc
sf2koryu
sf2m2
sf2m4
sf2m5
sf2m6
sf2m7
sf2rb
sf2rb2
sf2red
sf2t
sf2tj
sf2ua
sf2ub
sf2ud
sf2ue
sf2uf
sf2ui
sf2uk
sf2v004
sf2yyc
sfa
sfa2
sfa3
sfa3b
sfa3r1
sfach
sfar1
sfar2
sfar3
sfau
sfz2a
sfz2aa
sfz2ab
sfz2ah
sfz2aj
sfz2b
sfz2br1
sfz2h
sfz2j
sfz2n
sfz3a
sfz3ar1
sfz3j
sfz3jr1
sfz3jr2
sfza
sfzb
sfzbr1
sfzh
sfzj
sfzjr1
sfzjr2
sgemf
sgemfa
sgemfh
shadfrce
shadoww
shadowwa
shinobi
shinobi4
shippumd
shocktr2
shocktro
slammast
slammasu
slapbtjp
slapbtuk
slapfgtr
smbomb
smbombr1
snowbro2
snowbro3
snowbroa
snowbrob
snowbroc
snowbroj
snowbros
socbrawl
solomon
solomonj
sonicwi2
sonicwi3
spf2t
spf2ta
spf2xj
spinlbrj
spinlbrk
spinlbru
spinmast
ssf2
ssf2a
ssf2ar1
ssf2j
ssf2jr1
ssf2jr2
ssf2t
ssf2ta
ssf2tu
ssf2tur1
ssf2u
ssf2xj
ssideki
ssideki3
ssideki4
sstriker
sstrikra
stakwin
stakwin2
stratof
strhoop
strider
striderj
stridrja
stridrua
superman
superspy
supmodel
suprmanj
suprtrio
svc
svcpcb
swatpolc
tangtang
theroes
tigerhb1
tigerhb2
timesca1
timescan
tknight
tophunta
tophuntr
toppyrap
toryumon
tpgolf
trally
truxton
truxton2
tumbleb
tumbleb2
turbofrc
turfmast
twinadv
twinadvk
twinhawk
twinhwku
twinkle
twinspri
tws96
uecology
unsquad
uopoko
uopokoj
vampj
vampja
vampjr1
varth
varthj
varthr1
varthu
vhunt2
vhunt2r1
vhuntj
vhuntjr1
vhuntjr2
vsav
vsav2
vsava
vsavh
vsavj
vsavu
wakuwak7
wb3
wc90
wc90a
wc90t
wh1
wh1h
wh2
wh2j
whp
wildfang
willow
willowj
willowje
wintbob
wjammers
wlstar
wof
wofa
wofj
wofu
wonder3
wondl96
wrestwar
wwfwfest
wwfwfsta
wwfwfstb
wwfwfstj
xmcota
xmcotaa
xmcotah
xmcotaj
xmcotaj1
xmcotajr
xmcotau
xmvsf
xmvsfa
xmvsfar1
xmvsfb
xmvsfh
xmvsfj
xmvsfjr1
xmvsfjr2
xmvsfr1
xmvsfu
xmvsfur1
zedblade
zerowing
zintrckb
```

# Complete List of FBA-Libretro games

[FBA-Libretro Gamelist](https://raw.githubusercontent.com/libretro/fba-libretro/master/svn-current/trunk/gamelist.txt)