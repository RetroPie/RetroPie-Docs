To build binary archives of individual modules you can follow these steps:

Get sources, compile, install, configure and archive the package
```
sudo ./retropie_packages.sh builder module <MODULEID/MODULENAME>
```

You can configure, for which platform you want to build an archive by using the `__platform` variable. To build a module and a corresponding archive, e.g., for the Raspberry Pi 2, you use these command:
```
sudo ./retropie_packages.sh builder module <MODULEID/MODULENAME>
sudo ./retropie_packages.sh builder module <MODULEID/MODULENAME>
```

You can build binary archives of sections with

```
sudo ./retropie_packages.sh builder section <SECTIONNAME (eg core/opt/main/exp)>
```

Binary archives will end up in `~/RetroPie_Setup/tmp/archives`