# wallup
**Wall**paper **Up**dater:  
A bash script to update your gnome session desktop wallpaper periodically.

This script was developed on an Ubuntu desktop (16.04.3 LTS).  
It has most recently been tested on Ubuntu 20.04 and 22.04.  
It assumes that your login session will run gnome-shell.
You can check this using 'ps' to verify it is running.

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
You can edit the wallup script so that the variable WPDUAL is true.
This will utilize the ImageMagick function "convert" to merge two
images into a single side-by-side image for both monitors.
Be sure you have ImageMagick installed: `sudo apt install imagemagick`

### Stacked / Offset Dual Monitors
The branch **overhang** provides support for vertically stacked
monitors that are offset relative to each other. In this case, the
monitors are each 1920x1080 stacked vertically, with the top monitor
offset from the lower monitor by 1055 pixels.

This case is handled using a black rectangle PNG file (1055x1080)
that is attached to the right of the top monitor wallpaper image,
and to the left of the bottom monitor wallpaper image. The overhang
PNG image is named `overhang-blk.png` in this repository, but it
needs to be copied to `.../Wallpaper/.overhang-blk` for the wallup
script to use it. _(Note that the name begins with a dot and has no
extension.)_

### Running
Under normal usage, the script will autostart when you first log
on to the desktop. Alternatively, you can start the script from
the command line:  
`% ./wallup &`

Note that only one wallup script will run at a time. If the script
detects a newer invocation, the older invocation will terminate itself.
Also, the script will automatically terminate itself after you log out.

Activity is logged in the file "$HOME/Pictures/Wallpaper/.wpsave/wallup.log".

This script is provided freely and without any license.

**Kendall Auel**  
_January 26, 2018_  
_May 23, 2023_  
_October 12, 2023_
