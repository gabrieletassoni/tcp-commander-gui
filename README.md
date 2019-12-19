# Usage

Download the package for your OS from:

https://github.com/gabrieletassoni/tcp-commander-gui/packages

Double click on it to install or run it.

# config.json

This file is the one in which you can add your servers definitions.
On the first run of the application, no config.json is found, thus you have to drag&drop one on the gui.

A config.json example to command some PJLINK projectors in a lan, altogether, can be:

```json
[
    {
        "desc": "Nec NP-PX1005QL-B",
        "ip": "192.168.25.100",
        "port": 7142,
        "commands": {
            "on": "%1POWR 1\r",
            "off": "%1POWR 1\r"
        }
    },
    {
        "desc": "Sanyo PLC-HF10000L",
        "ip": "192.168.25.101",
        "port": 4352,
        "commands": {
            "on": "%1POWR 1\r"
        }
    },
    {
        "desc": "Sanyo PLC-HF10000L",
        "ip": "192.168.25.102",
        "port": 4352,
        "commands": {
            "on": "%1POWR 1\r",
            "off": "%1POWR 0\r"
        }
    }
]
```

Please note that the second projector listed, doesn't have an entry for the command "off", it will be queried by the application only if you push the "on" button.

# Development

All the commands are run from shell, in a GNU/Linux environment.

1. Clone this repository
2. Run ```yarn install```
3. Edit the files
4. Run ```node_modules/.bin/electron .``` to test your editing.

# Create package for your OS

This little app uses electron-forge, under the hoods, to create portable apps for Linux, MacOS, Windows

## All OSes

All the commands are run from shell, in a GNU/Linux environment.
This command will create a packaged releas for all the platforms configured in *package.json*

```shell
./node_modules/.bin/electron-forge publish
```

## Macos

```shell
./node_modules/.bin/electron-forge make -a x64 -p darwin
```

## Linux

```shell
./node_modules/.bin/electron-forge make -a x64 -p linux
```

## Windows

This command is for creating a 32bit application since the wine prefix I use for cross compiling is 32it.

```shell
./node_modules/.bin/electron-forge make -a ia32 -p win32
```

For windows, to be cross compiled on Linux, you need to setup wine with WINEPREFIX at 32bit.

### Wine Setup

All the commands are run from shell, in a GNU/Linux environment.

1. Remove any previously configured wine, if it's 64bit: ```rm -rf ~/.wine```
2. Create a new, clean, wine folder: ```WINEARCH=win32 wineboot```
3. Install dotnet: ```winetricks dotnet40```
