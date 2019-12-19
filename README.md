# Usage

Download the package for your OS from:

https://github.com/gabrieletassoni/tcp-commander-gui/packages

Double click on it to install or run it.

# Development

1. Clone this repository
2. Run ```yarn install```
3. Edit the files
4. Run ```node_modules/.bin/electron .``` to test your editing.

# Create package for your OS

This little app uses electron-forge, under the hoods, to create portable apps for Linux, MacOS, Windows

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