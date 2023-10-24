# wallup
**Wall**paper **Up**dater:  
A bash script to update your gnome session desktop wallpaper periodically.

This script was developed on an Ubuntu desktop (16.04.3 LTS).  
It has most recently been tested on Ubuntu 20.04 and 22.04.  
It assumes that your login session will run gnome-shell.
You can check this using 'ps' to verify it is running.

This script assumes you have ImageMagick installed, as it
uses the "convert" command to resize and possibly merge images.  
If necessary, install using: `sudo apt install imagemagick`

I have this configured as follows:

wallup : The bash script is copied to "/usr/local/bin":  
`% sudo cp wallup /usr/local/bin`

wallup.desktop : This file is copied to the autostart directory:  
`% cp wallup.desktop $HOME/.config/autostart`

By default, this script looks in "$HOME/Pictures/Wallpaper" for
the wallpaper images. Prior to running the script, you can set the
environment variable "WPHOME" to be the path to the wallpaper folder.
Alternatively, you can modify the default path in the script.

Place as many images as you like in the Wallpaper folder. They will
each be displayed in random order. After all images have been displayed
one time, another random sequence will begin.

The images change every 10 minutes (10 * 60 seconds). You will need
to modify the script to change this time interval.

### Dual Monitors
The script uses `xrandr --query` to determine the number and size
of monitors attached to the system. Currently, only the single
or dual monitor cases are supported.

### Stacked / Offset Dual Monitors
The script automatically detects the relative orientation of each
monitor and handles vertical, side-by-side, and offsets.

### Running
Under normal usage, the script will autostart when you first log
on to the desktop. Alternatively, you can start the script from
the command line:  
`% ./wallup &`

By default, the initial delay until the wallpaper is updated is
30 seconds. Subsequent updates are every 10 minutes by default,
as noted previously. The script takes a single parameter, the
delay in seconds before the first update. If you pass in a zero,
then you will also enable debug messages to the terminal:  
`% ./wallup 0`  
`Screen is 3840 pixels wide and 1171 pixels tall.`  
`Monitor1 is 1920 x 1080 + 1920 + 0`  
`There are two monitors connected to this system.`  
`Monitor2 is 1920 x 1080 + 0 + 91`  

Note that only one wallup script will run at a time. If the script
detects a newer invocation, the older invocation will terminate itself.
Also, the script will automatically terminate itself after you log out.

Activity is logged in the file **"$HOME/Pictures/Wallpaper/.wpsave/wallup.log"**.

This script is provided freely and without any license.

**Kendall Auel**  
_January 26, 2018_  
_May 23, 2023_  
_October 23, 2023_
