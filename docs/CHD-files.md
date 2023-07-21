## CHD

CHD is a lossless compression format originally developed for MAME, for the hard-drive contents of certain arcade machines. It has since been used in several other emulators as a means of storing CD-ROM game data. For CD-based games, it compresses the contents of a disc image (`.cue` + `.bin` files) to a single `.chd` file.

### Creating CHDs from CD-ROMs

`CHD` files can be created using the `chdman` program, developed by the [MAME project](https://mamedev.org).    
It is a command line application and creating a `.chd` file from an existing `.cue` is performed by running:

```shell
chdman createcd -i <game.cue> -o <game.chd>
```

To compress every file in a directory, use:

```shell
cd /path/to/folder
for i in *.cue; do chdman createcd -i "$i" -o "${i%.*}.chd"; done
```

To compress every file in subdirectories within a folder, use:

```shell
cd /path/to/folder
for i in */*.cue; do chdman createcd -i "$i" -o "${i%.*}.chd"; done
```


#### Windows

The following archive contains a MAME 0.205 version of CHDMAN and Windows batch files that can be used to quickly convert your PSX games to CHD (V5): [Download](https://drive.google.com/file/d/0B-ElaPpvBHs5aUd0QUM3c05kY2c/view?usp=sharing)

Run the appropriate batch file in the same folder as the ROM(s) you wish to compress, and it will search subfolders for `.cue` files to compress. If a `.chd` is not generated after running the appropriate batch, then something is wrong with the ROM(s) `.cue`.

#### MacOS

In MacOS, `chdman` can be installed through [Homebrew](https://brew.sh/), with the following command:

```shell
brew install rom-tools
```

#### Linux

On Debian based systems, including RetroPie, `chdman` can be found in the `mame-tools` package and can be installed with:

```shell
sudo apt install -y --no-install-recommends mame-tools
```
