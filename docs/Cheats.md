If you're like me, there are some games I could just never win as a kid. This guide will finally allow you to win! (albeit with a much lesser sense of satisfaction)

## Download Cheats

As a preface cheats only work through libretro/retroarch so take not of the emulators you are using.

You first need to open the RGUI. There are two ways of accessing the RGUI:

- In the **RetroPie** menu of EmulationStation select **Retroarch**
or
- Use the default hotkey combo **select+x** to open the rgui from within a game

Navigate to **Online Updater >> Update Cheats**

this will download a set of preconfigured cheat files for many games into `/opt/retropie/configs/all/retroarch/cheats`

### Enable Cheats

Now you can launch the game you want to finally win:

Open the RGUI with **select+x**

Choose **Quick Menu >> Cheats >> Load Cheat File**

Navigate to your game title and select it

Then navigate to the cheat you want to enable and press left or right to toggle in on/off

Select **Apply Cheat Changes**

Then press **B** to go out of the cheat menu and **resume** your game.

Your cheats should now be enabled

### Create Cheat Files

You can create .cht files in /opt/retropie/configs/all/retroarch/cheats/<system>/<rom_name>.cht

There are many different cheat files: the 3 main kinds are Game Genie, GameShark, and Action Replay. The following are examples of each kind:

#### Game Genie

Filename: `Addams Family, The - Pugsley's Scavenger Hunt (USA, Europe) (Game Genie).cht`

```
cheats = 3 

cheat0_desc = "Infinite Health"
cheat0_code = "009-15C"
cheat0_enable = false 

cheat1_desc = "Start With 9 Lives"
cheat1_code = "092-17F"
cheat1_enable = false 

cheat2_desc = "Infinite Lives"
cheat2_code = "004-27F"
cheat2_enable = false 
```

#### GameShark

Filename: `Addams Family, The (World) (GameShark).cht`
```
cheats = 3 

cheat0_desc = "Infinite Health"
cheat0_code = "011F68C0"
cheat0_enable = false 

cheat1_desc = "Infinite Ammo"
cheat1_code = "013FFAC1"
cheat1_enable = false 

cheat2_desc = "Infinite Lives"
cheat2_code = "010565C0"
cheat2_enable = false 
```

#### Action Replay

Filename: `Addams Family, The (USA, Europe) (Action Replay).cht`
```
cheats = 3 

cheat0_desc = "Infinite Lives"
cheat0_code = "FFA5D5:0005"
cheat0_enable = false 

cheat1_desc = "Infinite Hearts (Hits)"
cheat1_code = "FFA5D7:02"
cheat1_enable = false 

cheat2_desc = "Infinite/Max Money"
cheat2_code = "FFA5CF:99"
cheat2_enable = false 
```
### Multiline Cheat Codes

Filename: The Legend of the Dragoon

I want to use the following cheat for Infinite HP (All Characters):

```
D00CCDEC 1021
800CCDE0 0002
D00CCDEC 1021
800CCDE2 2401
D00CCDEC 1021
800CCDE4 0005
D00CCDEC 1021
800CCDE6 1027
D00CCDEC 1021
800CCDEE 2400
```

As you can see there are 10 codes which needs to be poked into the memory of the game.

If we simply want to use a Gameshark code we simply insert the Gameshark code as the code into the format. Except instead of the blank space we need to use a + So like this:
```
cheat0_desc = "Description"
cheat0_code = "800F45E6+2400"
cheat0_enable = false
```
If we have a multi address code like in our example, we MUST ONLY enter 1 address per cheat else it won't work. So coming back to our code for the Infinite HP for All Characters, we must add it as below to our cheat file:

```
cheat0_desc = "(1) Inf. HP In Battle"
cheat0_code = "D00CCDEC+1021"
cheat0_enable = false

cheat1_desc = "(2) Inf. HP In Battle"
cheat1_code = "800CCDE0+0002"
cheat1_enable = false

cheat2_desc = "(3) Inf. HP In Battle"
cheat2_code = "D00CCDEC+1021"
cheat2_enable = false

cheat3_desc = "(4) Inf. HP In Battle"
cheat3_code = "800CCDE2+2401"
cheat3_enable = false

cheat4_desc = "(5) Inf. HP In Battle"
cheat4_code = "D00CCDEC+1021"
cheat4_enable = false

cheat5_desc = "(6) Inf. HP In Battle"
cheat5_code = "800CCDE4+0005"
cheat5_enable = false

cheat6_desc = "(7) Inf. HP In Battle"
cheat6_code = "D00CCDEC+1021"
cheat6_enable = false

cheat7_desc = "(8) Inf. HP In Battle"
cheat7_code = "800CCDE6+1027"
cheat7_enable = false

cheat8_desc = "(9) Inf. HP In Battle"
cheat8_code = "D00CCDEC+1021"
cheat8_enable = false

cheat9_desc = "(10) Inf. HP In Battle"
cheat9_code = "800CCDEE+2400"
cheat9_enable = false
```