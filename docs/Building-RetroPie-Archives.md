To build archives of individual modules you can follow these steps:

1. Get sources, compile, install, configure the package:<br>`sudo ./retropie_packages.sh <MODULEID/MODULENAME>`
2. Build the archive:<br>`sudo ./retropie_packages.sh <MODULEID/MODULENAME> create_bin`

You can configure, for which platform you want to build an archive by using the `__platform` variable. To build a module and a corresponding archive, e.g., for the Raspberry Pi 2, you use these command:
```
sudo ./retropie_packages.sh <MODULEID/MODULENAME>
sudo ./retropie_packages.sh <MODULEID/MODULENAME> create_bin
```