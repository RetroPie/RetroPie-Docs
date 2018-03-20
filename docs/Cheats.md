If you're like me, there are some games I could just never win as a kid. This guide will finally allow you to win! (albeit with a much lesser sense of satisfaction)

## Download Cheats

As a preface cheats only work through libretro/retroarch so take note of the emulators you are using.

You first need to open the RGUI. There are two ways of accessing the RGUI:

- In the **RetroPie** menu of EmulationStation select **Retroarch**
or
- Use the default hotkey combo **select+x** to open the rgui from within a game

If you haven't done so already, you'll need to enable the advanced settings by navigating to **Settings >> User Interface >> Show Advanced Settings**

Navigate to **Online Updater >> Update Cheats**

this will download a set of preconfigured cheat files for many games into `/opt/retropie/configs/all/retroarch/cheats`

### Enable Cheats

Now you can launch the game you want to finally win:

Open the RGUI with **select+x**

Choose **Quick Menu >> Cheats >> Load Cheat File**

Navigate to your game title and select it

Then navigate to the cheat you want to enable and press left or right to toggle it on/off

Select **Apply Cheat Changes**

Then press **B** to go out of the cheat menu and **resume** your game.

Your cheats should now be enabled

### Create Cheat Files

You can create .cht files in `/opt/retropie/configs/all/retroarch/cheats/<system>/<rom_name>.cht`

The following is a reference chart for the types of cheat codes for each system:

| Console | Cheat type | Example code |
|---|---|---|
| Famicom / NES | Action Replay | 02A2:01 |
| Famicom / NES | Game Genie | APEETPEY |
| Game Boy | Game Genie | FA1-B9C-4C1 |
| Game Boy (Color) | GameShark | 0101CEC1 |
| Game Boy Advance | GameShark v3 | CD93194F 089CE0B4 |
| Game Boy Advance | GameShark v1/v2 | A62B1D67 EB2D |
| Game Gear | Action Replay | 00D3-C280 |
| Mega Drive / Genesis | Action Replay | FFFE21:0032 |
| Mega Drive / Genesis | Game Genie | NN8A-AADN |
| N64 | GameShark | 8033B177 0015 |
| NDS | Action Replay | 22085A50 00000001 |
| Sega Master System | Action Replay | 00C0-2502 |
| Super Famicom / SNES | Action Replay | 7E1490:FF |
| Super Famicom / SNES | Game Genie | 14B4-6F07 |


#### Cheat Code Example

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

#### Multiline Cheat Codes

The following is an example for a PSX game

Filename: `Resident Evil 2.cht`

```
cheats = 2

cheat0_desc = "Infinite Ammo Claire (1/2)"
cheat0_code = "800D49F5+0063"
cheat0_enable = "true"

cheat1_desc = "Infinite Ammo Claire (2/2)"
cheat1_code = "800D4A01+0063"
cheat1_enable = "true"
```

#### Mame Cheats

Mame has it's own configurations for cheats. You can see a guide [HERE](lr-mame2003#cheats)