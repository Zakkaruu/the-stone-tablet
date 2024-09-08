---
layout: page
title: Elden Ring Mods (ModEngine2) on Steamdeck
date: 2024-08-02 20:05:00
---

## Purpose
I spent quite some time trying to figure out how to gets mods to work on my Steamdeck, there were guides and alternative versions used, but I wanted to use the original mods. This guides demonstrates how to use the official ModLoader2 on Steamdeck with only a couple tweaks.

## Requirements
1. `Steamdeck`
2. `ModLoader2 v2.1.0`
    - https://github.com/soulsmods/ModEngine2/releases/download/release-2.1.0/ModEngine-2.1.0.0-win64.zip
3. `Elden Ring` installed on the default system drive.
4. Individual `mod` installation steps followed.

## Directions
- `Download and extract ModLoader2` to a location of your choice using the Desktop Mode of your Steamdeck.
- Edit the `launchmod_eldenring.bat` and replace its contents with:
```text
chcp 65001
:: The above line is necessary in case you edit this file to lead to a path with Unicode characters.
.\modengine2_launcher.exe -t er -c .\config_eldenring.toml --game-path "Z:/home/deck/.local/share/Steam/steamapps/common/ELDEN RING/Game/eldenring.exe"
```
- Add the batch file as a `non-Steam game`.
    - Change the `LAUNCH OPTIONS` to `STEAM_COMPAT_DATA_PATH="/home/deck/.local/share/Steam/steamapps/compatdata/1245620/" %command%`
- Follow individual mod directions on how to add them to ModLoader. 
    - DLL 'mods' need their file path to be added to the `config_eldenring.toml` file between the brackets in the `external_dlls = []` section. **Make sure to read the `.toml` file notes in the file. Especially regarding using `//` in file paths.**

## Advanced Notes
- You can create multiple `.bat` and `.toml` files with different sets of mods and dll files.
    - Duplicate the original `bat` and `toml` file and rename them as you see fit.
    - Modify the new `toml` file with mods and dlls as needed.
    - Modify the new `bat` file's `.\config_eldenring.toml` section with the name of the new `toml` file.
        - *e.g. new toml file name is `seamless.toml`.*
            - *Change `.\config_eldenring.toml` to `.\seamless.toml`*
    - Follow the previous directions for adding the new `bat` file as a `non-Steam game` and setting the `LAUNCH OPTIONS`.
- If you installed Elden Ring on a drive other than the system default, you will need to update the `--game-path` in the batch file.
- You can change the `STEAM_COMPAT_DATA_PATH` variable to another location to separate saves for each batch file you add.
    - For example
        - For regular mods/non-overhaul, like glorious merchant, seamless coop.
            -   `STEAM_COMPAT_DATA_PATH="/home/deck/.local/share/Steam/steamapps/compatdata/1245620/"`
        - For randomizers, or separate seamless randomizer saves
            - `STEAM_COMPAT_DATA_PATH="/home/deck/.local/share/Steam/steamapps/compatdata/1245620-1/"`
                - *Note the `-1` in the path `1245620-1`.*
                - I personally copy everything from the original compatdata folder to the new `-1` folder and delete the saves.
