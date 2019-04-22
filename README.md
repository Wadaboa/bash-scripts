# Bash scripts

## Installation
Below is an example on how to install the `dockerize` script:
1. Make a local clone of this repository in `~/scripts`
2. Copy `com.jobs.dockerize.plist` inside `/Library/LaunchAgents`
3. Open a terminal window and run `launchctl load /Library/LaunchAgents/com.jobs.dockerize.plist`
4. Open `System Preferences → Security & Privacy` and navigate to the `Privacy` tab
5. Click the “Lock” icon and enter your system password to unlock the panel settings
6. Click on `Full Disk Access` and add the `dockerize` executable to the list
7. Click on `Accessibility` and add the `dockerize` executable to the list

## Scripts
### dockerize
Script used to automate some tasks relative to docking/undocking the system to/from home/work.\
This script is a daemon, invoked when a specific USB device is connected/disconnected (In this case, this device is the external keyboard **Keyboard -- QuickFire XT**).\
So, whenever the **plugging event** happens, the script does the followings:
* If there's my external keyboard connected, changes keyboard layout from US to IT and enables bluetooth
* If there's an active ethernet connection, shuts down wifi
* If there are two connected external monitors, sets a dual wallpaper

And whenever the **unplugging event** happens, the script does the followings:
* If there isn't my external keyboard connected, changes keyboard layout from IT to US and disables bluetooth
* If there isn't an active ethernet connection, turns on wifi
* If there aren't two connected external monitors, sets a single wallpaper

The wallpapers are defined in the `assets` folder. The single monitor wallpaper is named `one.jpg`, while the dual monitor wallpapers are named `two_left.jpg` and `two_right.jpg`.

#### Dependencies
The script depends on the following libs:
* **xkbswitch** (https://github.com/myshov/xkbswitch-macosx)
* **blueutil** (https://github.com/toy/blueutil)
