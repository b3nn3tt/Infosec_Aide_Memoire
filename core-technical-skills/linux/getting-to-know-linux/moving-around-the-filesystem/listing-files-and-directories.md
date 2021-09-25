# Listing Files and Directories

The `ls` command is the most common command used to list information about files and directories.  
Many options available with the `ls` command allow you to gather different sets of files and directories as well as to view different kinds of information about them.

By default, when you type the `ls` command, the output shows you all **non-hidden files and directories** contained in the current directory. When you type `ls`, however, many Linux systems \(including Fedora and RHEL\) assign an alias `ls` to add options. To see if `ls` is aliased, enter the following:

```text
alias ls
```

![The --color=auto option causes different types of files and directories to be displayed in different colours.](../../../../.gitbook/assets/image%20%2812%29.png)

### List Example

Lets return to the `$HOME` directory, create a new directory called test, add a couple of different types of files, and then see what they look like with the ls command:

```text
cd $HOME
mkdir test; cd test
touch scriptx.sh apple
chmod 755 scriptx.sh
mkdir Stuff
ln -s apple pointer_to_apple
ls
```

![Example of ls with different file types](../../../../.gitbook/assets/image%20%288%29.png)

With the default `ls` alias in place, we can see that the directory `Stuff` shows up in blue, `pointer_to_apple` \(a symbolic link\) appears as aqua, and `scriptx.sh` \(which is an executable file\) appears in green. All other regular files show up in white. 

Typing `ls -l` to see a long listing of those files can make these different types of files clearer still:

```text
ls -l
```

![An example of a &quot;long listing&quot;](../../../../.gitbook/assets/image%20%2834%29.png)

Examining the long listing above, you will notice that the first character of each line shows the type of file:

*  - **-** indicates a regular file
* d - indicates a directory
* l - indicates a symbolic link

An executable file \(a script or binary file that runs as a command\) has execute bits turned on, `x` - more on this shortly...

We can also view "hidden files" - files or directories that a named with a `.` at the start - by adding the `-a` option to `ls`. A good example of this is a standard user's home directory, which contains a number of such files and directories:

![A long listing that also shows &quot;hidden&quot; files and directories](../../../../.gitbook/assets/image%20%281%29.png)

{% hint style="info" %}
Note that the `.` and `..` directories are listen when `-a` is used. A single . means "this directory". So, if you want to use a relative PATH to execute a binary that is in the current working directory \(and NOT in the PATH\), you preface the executables name with `./` .

The double `..` means "Parent Directory". So, you you were to execute the command `cd ..` , you would change your working directory to the parent directory of where you currently are.
{% endhint %}



