***
![psx](https://cloud.githubusercontent.com/assets/10035308/12213692/20e2fe3a-b63a-11e5-9e49-c47c33bc659d.png)
***
_The PlayStation 1 is a 5th generation video game console released by Sony in 1994._

***
## Emulators: [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed), [pcsx-rearmed](https://github.com/notaz/pcsx_rearmed)

## ROMS
Accepted File Extensions: **.bin .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx**

Place your PlayStation ROMs in 
```
/home/pi/RetroPie/roms/psx
````

## BIOS

The BIOS file is named **scph1001.BIN**

Place scph1001.BIN in
```
/home/pi/RetroPie/BIOS
```
See table at the bottom for alternative BIOS options that may or may not work.

## Controls

lr-pcsx-rearmed utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![playstation](https://cloud.githubusercontent.com/assets/10035308/8194532/8213433e-1439-11e5-8e69-87c6a7dc275c.png)

### Video Guide  

<a href="https://www.youtube.com/watch?v=a7JtysTXaAU
" target="_blank"><img src="https://i.ytimg.com/vi_webp/a7JtysTXaAU/mqdefault.webp" 
alt="RetroPie Playstation 1 emulation" width="300" height="190" border="10" /></a>  


### Alternative BIOS files

Add different bios' that you've tested and tell the community if it works or not.

Name |Description| md5          |        CRC32       | Comment
-----|----------|--------------|--------------------|-----------|------
ps-10j|SCPH-1000/DTL-H1000 (Version 1.0 J)|239665b1a3dade1b5a52c06338011044|3b601fc8||
ps-11j|SCPH-3000/DTL-H1000H (Version 1.1 01/22/95)|849515939161e62f6b866f6853006780|3539def6||
ps-20a|DTL-H1001 (Version 2.0 05/07/95 A)|dc2b9bf8da62ec93e868cfd29f0d067d|55847d8c||
ps-20e|DTL-H1002/SCPH-1002 (Version 2.0 05/10/95 E)|54847e693405ffeb0359c6287434cbef|9bb87c4b||
ps-21j|SCPH-3500 (Version 2.1 07/17/95 J)|cba733ceeff5aef5c32254f1d617fa62|bc190209||
ps-21a|DTL-H1101 (Version 2.1 07/17/95 A)|da27e8b6dab242d8f91a9b25d80c63b8|aff00f2f||
ps-21e|SCPH-1002/DTL-H1102 (Version 2.1 07/17/95 E)|417b34706319da7cf001e76e40136c23|86c30531||
ps-22j|SCPH-5000/DTL-H1200/DTL-H3000 (Version 2.2 12/04/95 J)|57a06303dfa9cf9351222dfcbb4a29d9|24fc7e17||
ps-22a|SCPH-1001/DTL-H1201/DTL-H3001 (Version 2.2 12/04/95 A)|924e392ed05558ffdb115408c263dccf|37157331||
ps-22e|SCPH-1002/DTL-H1202/DTL-H3002 (Version 2.2 12/04/95 E)|e2110b8a2b97a8e0b857a45d32f7e187|1e26792f||
ps-22d|DTL-H1100 (Version 2.2 03/06/96 D)|ca5cfc321f916756e3f0effbfaeba13b|decb22f5||
ps-30j|SCPH-5500 (Version 3.0 09/09/96 J)|8dd7d5296a650fac7319bce665a6a53c|ff3eeb8c||
ps-30a|SCPH-5501/SCPH-5503/SCPH-7003 (Version 3.0 11/18/96 A)|490f666e1afb15b7362b406ed1cea246|8d8cb7e4||
ps-30e|SCPH-5502/SCPH-5552 (Version 3.0 01/06/97 E)|32736f17079d0b2b7024407c39bd3050|d786f0b9||
ps-40j|SCPH-7000/SCPH-7500/SCPH-9000 (Version 4.0 08/18/97 J)|8e4c14f567745eff2f0408c8129f72a6|ec541cd0||
ps-41a|SCPH-7001/SCPH-7501/SCPH-7503/SCPH-9001/SCPH-9003/SCPH-9903 (Version 4.1 12/16/97 A)|1e68c231d0896b7eadcad1d7d8e76129|502224b6||
ps-41e|SCPH-7002/SCPH-7502/SCPH-9002 (Version 4.1 12/16/97 E)|b9d9a0286c33dc6b7237bb13cd46fdee|318178bf||
psone-43j|SCPH-100 (Version 4.3 03/11/00 J)|8abc1b549a4a80954addc48ef02c4521|f2af798b||
psone-44e|SCPH-102 (Version 4.4 03/24/00 E)|b10f5e0e3d9eb60e5159690680b1e774|0bad7ea9||
psone-45a|SCPH-101 (Version 4.5 05/25/00 A)|6e3735ff4c7dc899ee98981385f6f3d0|171bdcec||
psone-45e|SCPH-102 (Version 4.5 05/25/00 E)|de93caec13d1a141a40a79f5c86168d6|76b880e5||