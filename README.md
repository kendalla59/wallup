# wallup
Bash script to update your gnome session desktop wallpaper periodically.

This script was developed on an Ubuntu desktop (16.04.3 LTS).
It assumes that your login session will run gnome-session-binary.
You can check this using 'ps' to verify it is running.

I have this configured as follows:

wallup : The bash script is copied to "/usr/local/bin":
% sudo cp wallup /usr/local/bin

wallup.desktop : This file is copied to the autostart directory:
% cp wallup $HOME/.config/autostart

By default, this script looks in "$HOME/Pictures/Wallpaper" for
the wallpaper images. Prior to running the script, you can set the
environment variable "WPHOME" to be the path to the wallpaper folder.
Alternatively, you can modify the default path in the script.

Place as many images as you like in the Wallpaper folder. They will
each be displayed in random order. After all images have been displayed
one time, another random sequence will begin.

The images change every 10 minutes (10 * 60 seconds). You will need
to modify the script to change this time interval.

Under normal usage, the script will autostart when you first log
on to the desktop. Alternatively, you can start the script from
the command line:
% wallup &

Note that only one wallup script will run at a time. If the script
detects a newer invocation, the older invocation will terminate itself.
Also, the script will automatically terminate itself after you log out.

Activity is logged in the file "$HOME/Pictures/Wallpaper/.wpsave/wallup.log".

This script is provided freely and without any license.

Kendall Auel
January 26, 2018

