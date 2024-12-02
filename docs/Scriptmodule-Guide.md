# Scriptmodule Design Considerations

This document contains the "RetroPie-way" design guidelines for an emulator
scriptmodule.

It will not cover all aspects. Best way to learn on how to develop scriptmodules
is by learning from the existing ones.

## Overview

A scriptmodule (for an emulator, a port or libretro core) has the following major
function to cover. For this guide it is assumed that the emulator to be added is
"infini" for a system "smaky":

`function depends_infini()`

:   Should define all dependencies needed for the runtime and building the
    infini emulator. In this function `getDepends` installs Raspi-OS packages
    via apt for example.

`function sources_infini()`

:   Retrieves the sources which are needed to build the infini emulator. Typical
    functions called from here are `gitPullOrClone` and, if needed `applyPatch`. The
    sources will be put at `~/RetroPie-Setup/tmp/build/<infini-sourcetree>/`.

`function build_infini()`

:   Builds the binary (or binaries) needed to run the emulator. Build starts at
    the root of the sourcetree.

`function install_infini()`

:   Installs the emulator binaries, libretrocore or the files of a port into the
    RetroPie binary folders. For example:
    `/opt/retropie/emulators/infini/bin/<infini-executable>`,
    `/opt/retropie/libretrocores/lr-infini/infini_libretro.so` or `/opt/retropie/ports/infini/`

`function configure_infini()`

:   This function has the responsibility to glue the infini binary, the infini
    configuration (start directory, save games, ...) and the
    [runcommand-launcher](https://github.com/RetroPie/RetroPie-Setup/blob/master/scriptmodules/supplementary/runcommand.sh)
    together. The latter is called whenever you start a game from within the
    frontend, e.g. EmulationStation. This method is special as it is also called
    when infini is removed, thus not only during installation.


All these functions will be processed whenever you run: `sudo
./retropie_packages.sh infini`. You may also call them isolated, e.g. `sudo
./retropie_packages.sh infini configure`. Therefore it is important that each of
the functions is idempotent i.e, the result should always be identical
regardless if the function is called once or multiple times.

You can review the parameters for the different helper functions mentioned above
in the file [`helpers.sh`]() or generate a API documentation with:
```sh
for v in depends sources build; \
  do sudo ./retropie_packages.sh apidocs $v; \
done
```
Output will be in `~/RetroPie-Setup/tmp/build/apidocs/html/`.

## Documentation Header 

If you look at existing scriptmodules you will find these variables defined at
the beginning of the file. Fill them out with the information about the emulator
infini. In parenthesis the synopsis is shown.

`rp_module_id` (one word)

:   The ID of the scriptmodule. Most of the time it is safe to use the emulator
    name itself, thus as in this example infini. Keep the ID short and use only
    alphanumeric characters, plus dash (`-`) and underscore (`_`). The ID is
    also used for calling the scriptmodule directly from `retropie_packages.sh`
    script (see above).

`rp_module_desc` (one sentence)

:   Put here in quotes (`"`) a one-line description of the emulator. 

`rp_module_licence` (`HANDLE` `URL-to-verbatim-license`)

:   This property expects two parameters. One is a short handle for the license
    used for the emulator. Examples are GPL3 (GPL v3), NONCOM
    (Non-commercial). Define the handle UPPERCASE. The second parameter defines
    the full text to the license applied to the emulator. Both parameters are
    mandatory.

`rp_module_repo` (usually: three mandatory parameters, fourth optional)

:   This is the most complex property to fill out. The good part mainly it will
    be `git <git-repo-url> <branch>`. But let us begin from the start. First
    parameter is the type of source repo e.g., `git` or `svn`. Second is the URL
    of the repo you would usually use to clone a repository. The third parameter
    denotes the branch to be used (use `-` for Subversion based repos). The
    fourth parameter is optional and denotes the revision to check out of that
    branch. If no fourth parameter is given the HEAD revision will be checked
    out. If the emulator source repo uses different branches, depending for
    example on the architecture, you can also define a callback function. A
    callback function starts with a colon `:` followed by the function to be
    called. This function must be present in your scriptmodule. Use a leading
    underscore for your function to denote that it is an internally used
    function. You can find examples for callbacks for example in the
    [`dolphin.sh`](https://github.com/RetroPie/RetroPie-Setup/blob/master/scriptmodules/emulators/dolphin.sh)
    scriptmodule or
    [`mame.sh`](https://github.com/RetroPie/RetroPie-Setup/blob/master/scriptmodules/emulators/mame.sh)
    scriptmodule and others. You can also find the special operator `file` as
    first parameter if you browse through the scriptmodules but this option will
    not be covered here now.

`rp_module_help` (brief text)

:   Put here in quotes (`"`) a short info about where to put the ROMs, or if
    more complex user actions are needed after installation a link to the
    RetroPie-Docs for emulator infini. Obviously the linked documentation page
    should exist. Newlines in the displayed text can be forced with `\n`.

`rp_module_section` (predefined, pick one)

:   In which section will the emulator be collated? This is relevant when the
    user runs `retropie_setup.sh`. Most of the time you will use `exp` for
    experimental or `opt` for optional. If an scriptmodule emulator qualifies
    for the section `main` should be checked with the RetroPie maintainers
    first.

`rp_module_flags` (predefined, pick none to many)

:   Flags, as the name suggests, control under which conditions a scriptmodule
    can be run. Conditions may apply for the different hardwares, architectures
    and capabilities of an architecture. For example: A flag `sdl2` requires
    that on the target SDL2 must be available. If not the scriptmodule will not
    run. You can also negate a flag by putting a bang (`!`) before, thus
    `!armv6` would disallow to run the scriptmodule on Raspberry Pi Zero and
    Raspberry Pi One. See
    [here](https://en.wikipedia.org/wiki/Raspberry_Pi#Specifications) for
    detailed specification. Flags have an order and are a logical And
    conjunction. Use spaces to separate the flags. There is the special flag
    `all`, which when put negated at the beginning can be used to create a
    strict allow list, e.g. `!all 64bit` means this scriptmodule can only be run
    on 64-bit architectures. Grep through the existing scriptmodules to identify
    the current set of flags. If you assume to need a new flag, check with the
    RetroPie maintainers first.

## Major Predefined Variables

`$home`

:   The home directory of the account which is used to run any emulator.
    Default: `/home/pi/`

`$md_build`

:   The directory where the emulator is build. Default:
    `$home/RetroPie-Setup/tmp/build/$md_id`. Specific example: `/home/pi/RetroPie-Setup/tmp/build/infini`

`$md_conf_root`

:   The configuration root directory. Default: `/opt/retropie/config/`. Usually
    supplemented with the system name e.g., `mkUserDir $md_conf_root/smaky`.

`$md_data`

:   Location of extra files e.g., for building or installing the emulator.
    Mainly used to apply patches to the source tree before building.Default is
    sibling to your scriptmodule and concatenated with the `$repo_module_id` you
    have defined in the header (see above). For the emulator infini it would be:
    `$home/RetroPie-Setup/scriptmodules/emulators/infini/` with the scriptmodule
    path `$home/RetroPie-Setup/scriptmodules/emulators/infini.sh`. Scriptmodules
    for ports and libretrocores are kept below `ports/` and `libretrocores/`
    respectively instead of `emulators/`.

`$md_id`

:   Same as `$repo_module_id`

`$md_inst`

:   The installation target folder for the emulator:
    `/opt/retropie/emulators/$md_id/`. Or specific to this example:
    `/opt/retropie/emulators/infini/`

`$md_mode`

:   Mode in which the scriptmodule is running. Is `install` during installation
    or `remove` during removal of the emulator.

`$romdir`

:   Default: `/home/pi/RetroPie/roms/`. Make sure to add the system folder if
    you want to address the system's rom folder e.g., `$romdir/smaky`

`$user`

:   The user account running your emulator. Default: `pi`


## Design Notes

This section will cover some of the design best-practices and also desgin
choices you have to make with your scriptmodule.

### Build Options

The `make` should usually not contain any extra flags like `-j`. This is handled
by the script RetroPie script
[`system.sh`](https://github.com/RetroPie/RetroPie-Setup/blob/master/scriptmodules/system.sh).
You can however, define `__makeflags`, `__cflags`, aso. for the build if
required. In this case the predefined values are overridden. If you want to extend the build flags use the usual notation e.g., `CFLAGS+= <option>`.

### The Configuration Function 

The configuration function `function configure_infini()` is called during
installation and as well during removal of an emulator. Thus you most likely
have to add an `if` clause to avoid any file to be created during removal e.g.,
```sh
if [[ "$md_mode" == "install" ]]; then 
    ...
fi
```
In the configuration function you
may also define the launcher file.

#### Location of Launcher

Many emulators only require the absolute path to the ROM to launch. If the
emulator you are adressing with your scriptmodule requires different information
to start the emulator with the ROM you may use an lanucher file.

1. If the emulator has an own UI to add ROMs (like ScummVM) you should put it in
   `$romdir/<system>/` (e.g., `/home/pi/RetroPie/roms/smaky`) with the template
   filename `+Start ${md_id}.sh` (e.g., `+Start Infini.sh`), or
2. If the emulator always expects an ROM you put it in the folder `$md_inst`.
   The filename should be like `launcher_${md_id}.sh`.

As a rule of thumb try to keep the launcher file simple, but it should cover all
cases how an ROM file can be passed to the emulator or where the emulator
expects the ROM respective set of ROM files (e.g., subfolder). Document the
actions of the launcher, if they are not obvious.

Also avoid to introduce dependencies (in the function `depends_infini()`) for tools
which function can also be accomplished with the GNU tools (`sed`, `awk`, `tr`,
...) or with a small Python or Perl script.

!!! warning

    The launcher should not create any symbolic links or should otherwise rely on a
    Linux filesystem for the files in `$romdir`. As the `$romdir` may also be
    located on a exFAT filesystem or any other filesystem the usage of Linux
    filesystem commands like `ln -s` may cause the launcher to fail on non Linux
    filesystems.

#### Emulators's Configuration Folder

Some emulators do require a configuration folder, for example for save games or
emulator specific parameters which otherwise may clutter the command line call
of the emulator. Again some design decisions:

1. If the emulator provides a parameter to define the configuration folder use
   this switch and point it to `$md_conf_root/<system>/$md_id`, or
2. If there is no such option use the RetroPie function `moveConfigDir`. This
   example creates a symbolic link from `$home/.infini.cfg` to the target config
   file: 
   ```bash
   moveConfigFile "$home/.infini.cfg" "$md_conf_root/smaky/infini.cfg"
   ```

The usage of `XDG_...` variables (from the [XDG Base Directory
Specification](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html))
is discouraged, as it makes the configuration folder change less explicit and
may be not recognized in cases when the emulator is started without the launcher
e.g., during debugging purposes.

## Conclusion

This page introduced the nuts and bolts of scriptmodule design. Hopefully you
did learn something to get your scriptmodule compliant with the "RetroPie-way".
Please follow the 80-20 rule when creating a scriptmodule: Code is 80% of the
time read and only 20% of the time written: Make the intentions of the
scriptmodule clear and document the non obvious actions. 

There is more to discover than documented here, best is to review some of the
existing scriptmodules. If your are unsure or have a corner-case to discuss,
feel welcomed to place it in the RetroPie forum below "Ideas and Development".

Happy scripting and gaming!