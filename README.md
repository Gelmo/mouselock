# mouselock

A very simple script to toggle `xpointerbarrier` on and off

## Requirements

You must have [xpointerbarrier](https://www.uninformativ.de/git/xpointerbarrier) or [the xpointerbarrier fork](https://github.com/nogard0/xpointerbarrier) installed in your `PATH`

## Installation

This is just a bash script. Make it executable and put it wherever you want. I recommend adding it in a directory that's in your `PATH` and renaming the file from `mouselock.sh` to `mouselock`. Any examples in this README will assume you have done so.

### Arch Linux

An [AUR package](https://aur.archlinux.org/packages/mouselock) is available that installs [the xpointerbarrier fork](https://github.com/nogard0/xpointerbarrier) and places this script at `/usr/bin/mouselock`. Install it with your AUR helper of choice.

```
paru -S mouselock
```

## Usage

This script does not accept any arguments. You can set the `XPOINTER_ARGS` variable with any arguments you want to pass to `xpointerbarrier`. For example, you can set it in `~/.profile` for your user or in `/etc/environment` for all users, or you can set it while executing the script. Please refer to [the xpointerbarrier README](https://github.com/nogard0/xpointerbarrier/blob/main/README.md) for more information on the available arguments.

When this script is executed, it will run `xpointerbarrier` in the background unless it is already running. If `xpointerbarrier` is already running, it will be killed. You can run this script in a shell or you can execute it with a keyboard shortcut via your DE or WM (allowing for easy toggling). You can make a custom launch script or shortcut for any application that runs this script before launching the application, and then runs this script again (killing `xpointerbarrier`) after the application exits.

### Using with Steam games

Have an old game that doesn't lock the mouse to the fullscreen window? Add the following to the game's launch options in Steam:

```
mouselock; %command%; mouselock
```

#### Using a specific key to allow traversal to another screen

You can set the `XPOINTER_ARGS` variable when running this script to specify which key can be held to allow moving the mouse to another screen. Please refer to [the xpointerbarrier README](https://github.com/nogard0/xpointerbarrier/blob/main/README.md) for more information on the available arguments. This will also temporarily override the variable you've already set via your environment, allowing you to have one behavior globally for most games but have a different behavior for specific games (such as a game that uses the key you've set globally). This example uses the Win/Super key:

```
XPOINTER_ARGS="-w" mouselock; %command%; mouselock
```
