# Listing Files and Directories

The `ls` command is like your trusty torch in the maze-like filesystem – it lights up the contents of wherever you're standing. With it, you can look at, or "list" all the files and folders around you. `ls` has a bunch of options you can use to get a more detailed or different view.

Now, by just typing `ls` and pressing enter, you'll see a list of all the **non-secretive** items in your current location, otherwise known as the **current working directory**. However, some versions of Linux ([Fedora](https://fedoraproject.org/) and [RHEL](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux), for instance) like to be a bit clever. They've given `ls` a few additional settings right out of the box. To find out if your system has done something similar, you can try out the following command:

```
alias ls
```

![The --color=auto option causes different types of files and directories to be displayed in different colours.](<../../../../../.gitbook/assets/image (43).png>)

##

## List Example

Lets return to our `$HOME` directory, create a new directory called test, add a couple of different types of files, and then see what they look like with the `ls` command:

```
cd $HOME
mkdir test; cd test
touch scriptx.sh apple
chmod 755 scriptx.sh
mkdir Stuff
ln -s apple pointer_to_apple
ls
```

{% hint style="info" %}
Don't worry about the commands above for the moment as I'll cover them more comprehensively later - for now, just know that some new files were created and some permissions were set.
{% endhint %}

![Example of ls with different file types](<../../../../../.gitbook/assets/image (67).png>)

With the default `ls` alias in place, we can see that the directory `Stuff` shows up in blue, `pointer_to_apple` (a symbolic link, or "shortcut") appears as aqua, and `scriptx.sh` (which is an executable file) appears in green. All other regular files show up in white.

Typing `ls -l` to see a **long listing** of those files can make these different types of files clearer still:

```
ls -l
```

![An example of a "long listing"](<../../../../../.gitbook/assets/image (14).png>)

Examining the long listing above, you will notice that the first character of each line shows the type of file:

* \- : indicates a regular file
* d: indicates a directory
* l: indicates a symbolic link

An executable file (a script or binary file that runs as a command) has **execute bits** turned on, `x` - more on this shortly...

The `ls` command lets you peek at **hidden** files too; those that start with a dot `.` By using the `-a` option, you can unveil these hidden treasures. If you take a look at a typical user's home directory, you'll spot a bunch of these dot-prefixed files and directories, including the `.bashrc` file that we were looking at earlier on:

![A long listing that also shows "hidden" files and directories](<../../../../../.gitbook/assets/image (209).png>)

{% hint style="info" %}
Note at the top of the output that the `.` and `..` directories are listen when `-a` is used.&#x20;

A single `.` means **this directory**. So, if you want to use a relative PATH to execute a binary that is in the current working directory, and importantly, **NOT in the PATH**, you preface the executables name with `./`

The double `..` means **Parent Directory**. So, you you were to execute the command `cd ..` , you would change your working directory to the parent directory of where you currently are.
{% endhint %}
