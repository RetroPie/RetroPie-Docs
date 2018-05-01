## READ FIRST - Learning About PSP Emulation

Before moving on to the compatibility list, you should read [THIS](https://github.com/retropie/retropie-setup/wiki/Overclocking) Overclocking article entirely and read [THIS](https://github.com/RetroPie/RetroPie-Setup/wiki/Optimization-for-Nintendo-64#cpu-governor) CPU-Governor part of the N64 Optimization article. The former will explain everything you need to know about overclocking, while the latter is essential for smoother PSP emulation. [THESE](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP#ppsspp-1) tweaks mentioned in the PSP system article are also recommended for better PSP emulation.

PSP emulation on the Raspberry Pi is mostly restricted by the CPU processing power much like N64 emulation is restricted by the GPU processing power. Keeping that in mind, and that the PSP was released eight years after the N64, it is no surprise that most games just aren't in a playable state for low-end hardware. However, as the list will show, that doesn't mean there aren't a few games you can play on low-end hardware with some overclocking.

What this article intends to do is inform you which games can be played through overclocking by using the provided overclock as the baseline. Being able to match or even exceed the overclock provided should produce similar or improved results, while even if you aren't able to meet the overclock the initial results can be used to make informed decisions on which games to try.

## Contents

1. [Testing Method](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP-Compatibility-List#testing-method)
2. [Legend](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP-Compatibility-List#legend)
3. [PSP Compatibility List - Overclocked Raspberry Pi 3B - PPSSPP](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP-Compatibility-List#psp-compatibility-list---overclocked-raspberry-pi-3b---ppsspp)
4. [WiP - PSP Compatibility List - Overclocked Raspberry Pi 3B+ - PPSSPP](https://github.com/RetroPie/RetroPie-Setup/wiki/PSP-Compatibility-List#wip---psp-compatibility-list---overclocked-raspberry-pi-3b---ppsspp)

## Testing Method

The idea here is quite simple. Using the provided and *hopefully* easy to achieve overclock as a baseline, the games are tested by playing them and making sure all important gameplay elements are rendered properly. Games that run at full speed are marked as "Good". The games that run slightly below full speed or have slowdown intermittently are marked "Playable". Any games that have significant slowdown, don't render properly, or outright crash are marked as "Bad". In hindsight, the games should've been broken up into further categories, but hopefully some other contributor can address this.

Future contributors to this article should follow the previously used method (especially when it comes to using the provided overclock), but also improve upon the method to the best of their ability. Any game that is missing should be added to the appropriate list after testing to determine its status, while keeping to the ease of reading sorting method that the lists currently use. It is also advised to retest games marked previously as "Playable" or "Bad" whenever appropriate because PPSSPP is still actively developed and even the OS of the device used could get performance optimizations that improve the emulation.

## Legend

As you can see, the used classifications are far too simple for their own good, but the original list itself was a personal project and was only decided late into testing to be released publicly. The additional unused ones are suggestions for future contributors to use, while the temporary ones will hopefully be eliminated by contributors.

* Good - This game should run at full speed with the provided overclock and recommended tweaks, but may have cosmetic issues.
* Playable - This game either runs a little slow or performance drops intermittently throughout regular gameplay.
* Jittery - Currently non-existent, but a category that should've been used for certain games that have slowdown intermittently and were marked as "Playable" or even "Bad".
* Slow - Currently non-existent, but a category that should've been used for numerous games on this list that ran slow and were marked as "Bad" instead.
* Bad - This game runs too slow, doesn't render correctly, or outright crashes.
* Crash - Currently non-existent, but a category that should've been used for a few games that outright crash.
* Untested - Self-explanatory. Hopefully a temporary category on this list and currently exists solely on the the WiP Pi 3B+ list.
* Overclocked Pi 3B+ Candidate - Another hopefully temporary category on this list for simply any game that the list author felt had a good chance of becoming "Playable" or "Good" on a Pi 3B+.

## PSP Compatibility List - Overclocked Raspberry Pi 3B - PPSSPP

The following overclock was used for testing the games on the following list, with the CPU-Governor tweak from the N64 Optimization article and the tweaks from the PSP system article being used as well. It is certainly possible to exceed this overclock and make a few more games marked as "Playable" on this list to reach a "Good" status, but don't expect any game under "Bad" to become "Playable" unless PPSSPP improves said game's emulation significantly.

### Overclock Example
* arm_freq=1350
* gpu_freq=500
* core_freq=550
* sdram_freq=550
* over_voltage=5
* sdram_over_voltage=4

| Title | Status |
| :---: | :---: |
|  2D Adventures of Rotating Octopus Character, The (USA) (Minis) | Good |
|  Ape Academy 2 (Europe) | Good |
|  Ape Escape - On the Loose (USA) | Good |
|  Ape Escape Academy (USA) | Good |
|  Beaterator (USA) | Good |
|  Blast Off (USA) (Minis) | Good |
|  BlazBlue Calamity Trigger (USA) | Good |
|  BlazBlue Continuum Shift II (USA) | Good |
|  Bomberman (USA) | Good |
|  Bomberman Land (USA) | Good |
|  Castlevania Dracula X Chronicles (USA) | Good |
|  Crisis Core Final Fantasy VII (USA) | Good |
|  CRUSH (USA) | Good |
|  Disgaea - Afternoon of Darkness (USA) | Good |
|  Disgaea 2 - Dark Hero Days (USA) | Good |
|  Disgaea Infinite (USA) | Good |
|  Every Extend Extra (USA) | Good |
|  Final Fantasy III (USA) | Good |
|  Ghost in the Shell - Stand Alone Complex (USA) | Good |
|  Half Minute Hero (USA) | Good |
|  Hot Shots Tennis Get A Grip (USA) | Good |
|  Legend of Heroes 2 - Prophecy of the Moonlight Witch (USA) | Good |
|  Loco Roco (USA) | Good |
|  Loco Roco 2 (USA) | Good |
|  Lumines (USA) | Good |
|  Lumines II (USA) | Good |
|  Marvel Trading Card Game (USA) | Good |
|  Mega Man - Powered Up (USA) | Good |
|  Mega Man X - Maverick Hunter (USA) | Good |
|  Metal Gear Acid (USA) | Good |
|  Metal Gear Solid - Digital Graphic Novel (USA) | Good |
|  Metal Slug XX (USA) | Good |
|  Patapon (USA) | Good |
|  Patapon 3 (USA) | Good |
|  Persona (USA) | Good |
|  Persona 2 - Innocent Sin (USA) | Good |
|  Pinball Fantasies (USA) (Minis) | Good |
|  Pinball Hall of Fame - The Gottlieb Collection (USA) | Good |
|  Pinball Hall of Fame - The Williams Collection (USA) | Good |
|  Pixel Junk Monsters Deluxe (USA) | Good |
|  Power Stone Collection (USA) | Good |
|  Puzzle Quest - Challenge of the Warlords (USA) | Good |
|  Rainbow Islands Evolution (USA) | Good |
|  Sid Meier's Pirates! (USA) | Good |
|  Space Invaders Extreme (USA) | Good |
|  Space Shooter for 2 Bucks!, A (USA) (Minis) | Good |
|  Street Fighter Alpha 3 MAX (USA) | Good |
|  Tetris (USA) (Minis) | Good |
|  Ys - The Oath in Felghana (USA) | Good |
|  Ys 6 - The Ark of Napishtim (USA) | Good |
|  Ys I and II Chronicles (USA) | Good |
|  ZHP - Unlosing Ranger vs Darkdeath Evilman (USA) | Good |
|  Final Fantasy (USA) | Playable |
|  Final Fantasy IV - The Complete Collection (USA) | Playable |
|  Ghostbusters (USA) | Playable |
|  Grand Theft Auto Chinatown Wars (USA) | Playable |
|  LEGO Star Wars II - The Original Trilogy (USA) | Playable |
|  Little Big Planet (USA) | Playable |
|  Modnation Racers (USA) | Playable |
|  Pac-Man World 3 (USA) | Playable |
|  Pac-Man World Rally (USA) | Playable |
|  Persona 3 Portable (USA) | Playable |
|  Pro Evolution Soccer 2007 (USA) | Playable |
|  Ratatouille (USA) | Playable |
|  Rockman Dash - Hagane no Boukenshin (Japan) | Playable |
|  Rockman Dash 2 (Japan) | Playable |
|  Sega Genesis Collection (USA) | Playable |
|  Snoopy vs The Red Baron (USA) | Playable |
|  Soul Calibur - Broken Destiny (USA) | Playable |
|  Spiderman - Web of Shadows (USA) | Playable |
|  Spongebob - Truth or Square (USA) | Playable |
|  Toy Story 3 (USA) | Playable |
|  Worms - Open Warfare (USA) | Playable |
|  Xiaolin Showdown (USA) | Playable |
|  2010 FIFA World Cup South Africa (USA) | Bad |
|  Bubble Bobble Evolution (USA) | Bad |
|  Burnout Dominator (USA) | Bad |
|  Burnout Legends (USA) (Greatest Hits) | Bad |
|  Crash Mind Over Mutant (USA) | Bad |
|  Crash of the Titans (USA) | Bad |
|  Crash Team Racing (USA) | Bad |
|  Crazy Taxi - Fare Wars (USA) | Bad |
|  Daxter (USA) | Bad |
|  Dissidia 012 Duodecim Final Fantasy (USA) | Bad |
|  Dissidia Final Fantasy (USA) | Bad |
|  Field Commander (USA) | Bad |
|  FIFA Soccer 07 (USA) | Bad |
|  FIFA Soccer 09 (USA) | Bad |
|  Final Fantasy II (USA) | Bad |
|  Final Fantasy Tactics - The War of the Lions (USA) | Bad |
|  Gitaroo Man Lives (USA) | Bad |
|  God of War - Chains of Olympus (USA) | Bad |
|  God of War - Ghost of Sparta (USA) | Bad |
|  Gran Turismo (USA) | Bad |
|  Grand Theft Auto Liberty City Stories (USA) | Bad |
|  Grand Theft Auto Vice City Stories (USA) | Bad |
|  Growlanser - Wayfarer of Time (USA) | Bad |
|  Growlanser - Wayfarer of Time (USA) [UNDUB v1.01] | Bad |
|  Hot Shot Golf Open Tee (USA) (v1.1) | Bad |
|  Hot Shots Golf Open Tee 2 (USA) | Bad |
|  Jak and Daxter - The Lost Frontier (USA) | Bad |
|  Jeanne Darc (USA) | Bad |
|  Killzone Liberation (USA) | Bad |
|  Kingdom Hearts - Birth by Sleep (USA) | Bad |
|  Kingdom Hearts - Birth by Sleep Final Mix (Japan) | Bad |
|  Legend of Heroes - Trails in the Sky (USA) | Bad |
|  Legend of Heroes (USA) | Bad |
|  Legend of Heroes 3 - Song of the Ocean (USA) | Bad |
|  Lunar - Silver Star Harmony (USA) | Bad |
|  Manhunt 2 (USA) [Uncensored] | Bad |
|  Marvel Ultimate Alliance (USA) | Bad |
|  Marvel Ultimate Alliance 2 (USA) | Bad |
|  Medievil Resurrection (USA) | Bad |
|  Megamind - The Blue Defender (USA) | Bad |
|  Metal Gear Acid 2 (USA) | Bad |
|  Metal Gear Solid - Peace Walker (USA) | Bad |
|  Metal Gear Solid - Portable Ops (USA) | Bad |
|  Metal Gear Solid - Portable Ops Plus (USA) | Bad |
|  Metal Slug Anthology (USA) | Bad |
|  MLB (USA) | Bad |
|  MLB 06 - The Show (USA) | Bad |
|  MLB 07 - The Show (USA) | Bad |
|  Monster Hunter Freedom (USA) | Bad |
|  Monster Hunter Freedom 2 (USA) | Bad |
|  Monster Hunter Freedom Unite (USA) | Bad |
|  MotorStorm Arctic Edge (USA) | Bad |
|  NBA Live 06 (USA) | Bad |
|  OutRun 2006 - Coast 2 Coast (USA) | Bad |
|  Patapon 2 (USA) | Bad |
|  Pursuit Force (USA) | Bad |
|  Race Driver 2006 (USA) | Bad |
|  Ratchet and Clank - Size Matters (USA) | Bad |
|  Resistance Retribution (USA) | Bad |
|  Ridge Racer (USA) | Bad |
|  Riff Everyday Shooter (Europe) (PSN) | Bad |
|  Rock Band Unplugged (USA) | Bad |
|  Secret Agent Clank (USA) | Bad |
|  Sega Rally Revo (USA) | Bad |
|  Simpsons Game, The (USA) | Bad |
|  SOCOM US Navy SEALs - Fireteam Bravo (USA) | Bad |
|  SOCOM US Navy SEALs - Fireteam Bravo 2 (USA) | Bad |
|  SOCOM US Navy SEALs - Fireteam Bravo 3 (USA) | Bad |
|  SOCOM US Navy SEALs - Tactical Strike (USA) | Bad |
|  Spiderman - Friend or Foe (USA) | Bad |
|  Spiderman 2 (USA) | Bad |
|  Spiderman 3 (USA) | Bad |
|  Split Second Velocity (USA) | Bad |
|  SpongeBob Squarepants - The Yellow Avenger (USA) | Bad |
|  Star Ocean - First Departure (USA) | Bad |
|  Star Ocean - Second Evolution (USA) | Bad |
|  Star Wars - Battlefront - Elite Squadron (USA) | Bad |
|  Star Wars - Battlefront - Renegade Squadron (USA) | Bad |
|  Star Wars - Lethal Alliance (USA) | Bad |
|  Star Wars - The Clone Wars - Republic Heroes (USA) | Bad |
|  Star Wars - The Force Unleashed (USA) | Bad |
|  Super Monkey Ball Adventure (USA) | Bad |
|  Syphon Filter - Dark Mirror (USA) | Bad |
|  Syphon Filter - Logans Shadow (USA) | Bad |
|  Tactics Ogre - Let Us Cling Together (USA) | Bad |
|  Tekken - Dark Resurrection (USA) | Bad |
|  Tekken 6 (USA) | Bad |
|  Test Drive Unlimited (USA) | Bad |
|  Tiger Woods PGA Tour 06 (USA) | Bad |
|  Tomb Raider Anniversary (USA) | Bad |
|  Tomb Raider Legend (USA) | Bad |
|  Tony Hawks Underground 2 Remix (USA) | Bad |
|  Transformers - Revenge of the Fallen (USA) | Bad |
|  Transformers - The Game (USA) | Bad |
|  Ultimate Ghosts N Goblins (USA) | Bad |
|  Valkyria Chronicles 2 (USA) | Bad |
|  Valkyrie Profile - Lenneth (USA) | Bad |
|  Valkyrie Profile - Lenneth (USA) [UNDUB] | Bad |
|  Virtua Tennis - World Tour (USA) | Bad |
|  Virtua Tennis 3 (USA) | Bad |
|  Wall-E (USA) | Bad |
|  Warriors, The (USA) | Bad |
|  Where is My Heart (USA) (Minis) | Bad |
|  Wipeout Pulse (USA) | Bad |
|  Wipeout Pure (Greatest Hits) (USA) | Bad |
|  Worms - Open Warfare 2 (USA) | Bad |
|  WWE Smackdown vs Raw 2006 (USA) | Bad |
|  X-Men Legends II - Rise of Apocolypse (USA) | Bad |
|  X-Men Origins - Wolverine (USA) | Bad |
|  Ys Seven (USA) | Bad |

## WiP - PSP Compatibility List - Overclocked Raspberry Pi 3B+ - PPSSPP

First of all, this list is here for someone else to complete. The original author of this page didn't own a Pi 3B+, but saw fit to start this part for another contributor with a Pi 3B+ to begin work on. If you reading this happen to own a Pi 3B+, then please consider contributing by testing games below on an overclock similar to the one for the Pi 3B above except with a higher "arm_freq" that the Pi 3B+ is capable of.

Try to keep the overclock realistic and not some fine tuned overclock within 5 or 2 of the CPU becoming unstable. Something like keeping to increments of 25 seems reasonable.

As you can see, this list begins at the previous list's "Playable" status games. The reason for this is quite simply that any games that ran well enough to be marked "Good" on an overclocked Pi 3B should continue to run well on an overclocked Pi 3B+ and there is no need for the repetition. Anything marked "Playable" should have an excellent chance of changing to a "Good" status on a Pi 3B+.

Another thing you'll notice is that almost all games previously marked "Bad" have been changed to "Untested", while a few have been marked "Overclocked Pi 3B+ Candidate". "Bad" being changed to "Untested" is self-explanatory, but the ones marked "Overclocked Pi 3B+ Candidate" are games that the author of this list felt were good choices for a Pi 3B+ owner to test first.

| Title | Status |
| :---: | :---: |
|  Final Fantasy (USA) | Playable |
|  Final Fantasy IV - The Complete Collection (USA) | Playable |
|  Ghostbusters (USA) | Playable |
|  Grand Theft Auto Chinatown Wars (USA) | Playable |
|  LEGO Star Wars II - The Original Trilogy (USA) | Playable |
|  Little Big Planet (USA) | Playable |
|  Modnation Racers (USA) | Playable |
|  Pac-Man World 3 (USA) | Playable |
|  Pac-Man World Rally (USA) | Playable |
|  Persona 3 Portable (USA) | Playable |
|  Pro Evolution Soccer 2007 (USA) | Playable |
|  Ratatouille (USA) | Playable |
|  Rockman Dash - Hagane no Boukenshin (Japan) | Playable |
|  Rockman Dash 2 (Japan) | Playable |
|  Sega Genesis Collection (USA) | Playable |
|  Snoopy vs The Red Baron (USA) | Playable |
|  Soul Calibur - Broken Destiny (USA) | Playable |
|  Spiderman - Web of Shadows (USA) | Playable |
|  Spongebob - Truth or Square (USA) | Playable |
|  Toy Story 3 (USA) | Playable |
|  Worms - Open Warfare (USA) | Playable |
|  Xiaolin Showdown (USA) | Playable |
|  Crash Mind Over Mutant (USA) | Overclocked Pi 3B+ Candidate |
|  Crash of the Titans (USA) | Overclocked Pi 3B+ Candidate |
|  Daxter (USA) | Overclocked Pi 3B+ Candidate |
|  Final Fantasy II (USA) | Overclocked Pi 3B+ Candidate |
|  Medievil Resurrection (USA) | Overclocked Pi 3B+ Candidate |
|  Metal Gear Solid - Portable Ops (USA) | Overclocked Pi 3B+ Candidate |
|  Metal Gear Solid - Portable Ops Plus (USA) | Overclocked Pi 3B+ Candidate |
|  Tekken - Dark Resurrection (USA) | Overclocked Pi 3B+ Candidate |
|  2010 FIFA World Cup South Africa (USA) | Untested |
|  Bubble Bobble Evolution (USA) | Untested |
|  Burnout Dominator (USA) | Untested |
|  Burnout Legends (USA) (Greatest Hits) | Untested |
|  Crash Team Racing (USA) | Untested |
|  Crazy Taxi - Fare Wars (USA) | Untested |
|  Dissidia 012 Duodecim Final Fantasy (USA) | Untested |
|  Dissidia Final Fantasy (USA) | Untested |
|  Field Commander (USA) | Untested |
|  FIFA Soccer 07 (USA) | Untested |
|  FIFA Soccer 09 (USA) | Untested |
|  Final Fantasy Tactics - The War of the Lions (USA) | Untested |
|  Gitaroo Man Lives (USA) | Untested |
|  God of War - Chains of Olympus (USA) | Untested |
|  God of War - Ghost of Sparta (USA) | Untested |
|  Gran Turismo (USA) | Untested |
|  Grand Theft Auto Liberty City Stories (USA) | Untested |
|  Grand Theft Auto Vice City Stories (USA) | Untested |
|  Growlanser - Wayfarer of Time (USA) | Untested |
|  Growlanser - Wayfarer of Time (USA) [UNDUB v1.01] | Untested |
|  Hot Shot Golf Open Tee (USA) (v1.1) | Untested |
|  Hot Shots Golf Open Tee 2 (USA) | Untested |
|  Jak and Daxter - The Lost Frontier (USA) | Untested |
|  Jeanne Darc (USA) | Untested |
|  Killzone Liberation (USA) | Untested |
|  Kingdom Hearts - Birth by Sleep (USA) | Untested |
|  Kingdom Hearts - Birth by Sleep Final Mix (Japan) | Untested |
|  Legend of Heroes - Trails in the Sky (USA) | Untested |
|  Legend of Heroes (USA) | Untested |
|  Legend of Heroes 3 - Song of the Ocean (USA) | Untested |
|  Lunar - Silver Star Harmony (USA) | Untested |
|  Manhunt 2 (USA) [Uncensored] | Untested |
|  Marvel Ultimate Alliance (USA) | Untested |
|  Marvel Ultimate Alliance 2 (USA) | Untested |
|  Megamind - The Blue Defender (USA) | Untested |
|  Metal Gear Acid 2 (USA) | Untested |
|  Metal Gear Solid - Peace Walker (USA) | Untested |
|  Metal Slug Anthology (USA) | Untested |
|  MLB (USA) | Untested |
|  MLB 06 - The Show (USA) | Untested |
|  MLB 07 - The Show (USA) | Untested |
|  Monster Hunter Freedom (USA) | Untested |
|  Monster Hunter Freedom 2 (USA) | Untested |
|  Monster Hunter Freedom Unite (USA) | Untested |
|  MotorStorm Arctic Edge (USA) | Untested |
|  NBA Live 06 (USA) | Untested |
|  OutRun 2006 - Coast 2 Coast (USA) | Untested |
|  Patapon 2 (USA) | Untested |
|  Pursuit Force (USA) | Untested |
|  Race Driver 2006 (USA) | Untested |
|  Ratchet and Clank - Size Matters (USA) | Untested |
|  Resistance Retribution (USA) | Untested |
|  Ridge Racer (USA) | Untested |
|  Riff Everyday Shooter (Europe) (PSN) | Untested |
|  Rock Band Unplugged (USA) | Untested |
|  Secret Agent Clank (USA) | Untested |
|  Sega Rally Revo (USA) | Untested |
|  Simpsons Game, The (USA) | Untested |
|  SOCOM US Navy SEALs - Fireteam Bravo (USA) | Untested |
|  SOCOM US Navy SEALs - Fireteam Bravo 2 (USA) | Untested |
|  SOCOM US Navy SEALs - Fireteam Bravo 3 (USA) | Untested |
|  SOCOM US Navy SEALs - Tactical Strike (USA) | Untested |
|  Spiderman - Friend or Foe (USA) | Untested |
|  Spiderman 2 (USA) | Untested |
|  Spiderman 3 (USA) | Untested |
|  Split Second Velocity (USA) | Untested |
|  SpongeBob Squarepants - The Yellow Avenger (USA) | Untested |
|  Star Ocean - First Departure (USA) | Untested |
|  Star Ocean - Second Evolution (USA) | Untested |
|  Star Wars - Battlefront - Elite Squadron (USA) | Untested |
|  Star Wars - Battlefront - Renegade Squadron (USA) | Untested |
|  Star Wars - Lethal Alliance (USA) | Untested |
|  Star Wars - The Clone Wars - Republic Heroes (USA) | Untested |
|  Star Wars - The Force Unleashed (USA) | Untested |
|  Super Monkey Ball Adventure (USA) | Untested |
|  Syphon Filter - Dark Mirror (USA) | Untested |
|  Syphon Filter - Logans Shadow (USA) | Untested |
|  Tactics Ogre - Let Us Cling Together (USA) | Untested |
|  Tekken 6 (USA) | Untested |
|  Test Drive Unlimited (USA) | Untested |
|  Tiger Woods PGA Tour 06 (USA) | Untested |
|  Tomb Raider Anniversary (USA) | Untested |
|  Tomb Raider Legend (USA) | Untested |
|  Tony Hawks Underground 2 Remix (USA) | Untested |
|  Transformers - Revenge of the Fallen (USA) | Untested |
|  Transformers - The Game (USA) | Untested |
|  Ultimate Ghosts N Goblins (USA) | Untested |
|  Valkyria Chronicles 2 (USA) | Untested |
|  Valkyrie Profile - Lenneth (USA) | Untested |
|  Valkyrie Profile - Lenneth (USA) [UNDUB] | Untested |
|  Virtua Tennis - World Tour (USA) | Untested |
|  Virtua Tennis 3 (USA) | Untested |
|  Wall-E (USA) | Untested |
|  Warriors, The (USA) | Untested |
|  Where is My Heart (USA) (Minis) | Untested |
|  Wipeout Pulse (USA) | Untested |
|  Wipeout Pure (Greatest Hits) (USA) | Untested |
|  Worms - Open Warfare 2 (USA) | Untested |
|  WWE Smackdown vs Raw 2006 (USA) | Untested |
|  X-Men Legends II - Rise of Apocolypse (USA) | Untested |
|  X-Men Origins - Wolverine (USA) | Untested |
|  Ys Seven (USA) | Untested |