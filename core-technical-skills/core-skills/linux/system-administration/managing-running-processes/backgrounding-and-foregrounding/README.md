# Backgrounding and Foregrounding

If you are using Linux over a network or from a dumb terminal (a monitor that allows only text input with no GUI support), your shell may be all that you have. You may be used to a graphical environment in which you have lots of programs active at the same time so that you can switch among them as needed. This shell thing can seem pretty limited.

Although the bash shell doesn’t include a GUI for running many programs at once, it does let you move active programs between the background and foreground. In this way, you can have lots of stuff running and selectively choose the one you want to deal with at the moment.

You can place an active program in the background in several ways:

* Add an ampersand (**`&`**) to the end of a command line when you first run the command\

* You can also use the at (`@`) command to run commands in such a way that they are not connected to the shell\

* To stop a running command and put it in the background, press `Ctrl` + `Z`\

* After the command is stopped, you can either bring it back into the foreground with the `fg` command, or start it running in the background with the `bg` command

Keep in mind that any command running in the background might spew output during commands that you run subsequently from that shell (try a `ping` command, you'll see what I mean). For example, if output appears from a command running in the background during a vi session, simply press `Ctrl` + `L` to redraw the screen to get rid of the output - you can always try **2> /dev/null** as an alternative...
