# Shell Commands

The simplest way to run a command is to simply type its name into the terminal and hit enter. Commands are small programs, often dubbed binaries or executables (akin to a .exe in Windows), that the shell "**calls**" (finds and runs) - this is commonly known as command execution.

Commands, for the most part, have a similar syntax that it generally goes like this:

```
[command name] [option] [argument]
```

Instead of chucking a massive list of commands at you now, I'll weave them in as we go along, explaining each as they pop up. For now, we're going to hone in on the art of command management.

##

## PATH

By now, you've played with a few commands like `cat`, `grep`, and `chsh`. You might be scratching your head thinking, "_Where do these commands come from?_" or "_How on earth does the shell execute the commands I type?_". The magic behind this is called the **PATH**.&#x20;

In essence, the **PATH** is a list of directories nestled within the Linux File System (LFS). Each time you type a command, the shell looks through this list and if the command is found, it executes. Pretty simple, right?

{% hint style="info" %}
Remember a moment ago when I said that the shell "**calls**" the command. Well, if you consider the **PATH** as an old school telephone book that lists where applications "live", then you are looking up their number and literally calling them...\


Im not sure that's the intended analogy, but it works for me!
{% endhint %}

So, it begs the question, "_What's actually in the PATH?_". The directories that make up the **PATH** are stored in a shell environment variable in much the same way as the current running shell we saw previously. Therefore, it can be viewed in much the same way:

```
echo $PATH
```

![An example of the contents of the $PATH variable](<../../../../../../.gitbook/assets/image (23).png>)

As you can see, a list of directories is displayed, each separated by a colon (`:`).&#x20;

### <mark style="color:red;">**The path directory order is important**</mark>

When you enter the name of a command, and the shell looks to the PATH, the listed directories are checked from **left to right**. Consider the following scenario:

We enter the command `test`. The shell attempts to call the `test` command and so consults the **PATH**. In doing so, it discovers that multiple binaries named `test` exists in multiple directories:

&#x20;    `/usr/local/sbin`\
\
&#x20;    `/bin` \
\
So, which version of `test` is executed?

In this scenario, the binary present in `/usr/local/sbin` is executed as it is present within a directory earlier (**leftmost**) in the list.

&#x20;   "_But what if I want to execute `test` from `/bin` rather than from `/usr/local/sbin?`_"...

To override the natural behaviour of the shell, you can specify the exact location of the desired binary you wish to execute by typing out its full location within the LFS - this is properly known as the **Absolute Path**:

```
/bin/test
```

Alternatively, you can modify the order of the **PATH** variable to ensure the correct binary is called by the shell.

{% hint style="info" %}
In contrast to certain other operating systems, Linux doesn't initially scan the present directory for an executable before referencing the PATH. Instead, it sets off scouring the PATH right away.



To run executables present in the current directory, they either have to be mentioned in the PATH, or you must provide their absolute (like `/home/user/scriptx.sh`) or relative path (e.g., `./scriptx.sh`). We'll circle back to the notions of Absolute and Relative PATHs shortly...
{% endhint %}

##

## Locate Commands in PATH with `which`

Suppose you're certain about the command you intend to use, but you want to know precisely where within the LFS it resides. For that, we turn to the `which` command:

```
which COMMAND
```

![Example of the which command](<../../../../../../.gitbook/assets/image (28).png>)

{% hint style="info" %}
When you execute the `which` command, it will look in each directory specified in PATH for any binary file that has a corresponding name. However, if there is a "**Symbolic Link**" to a command (the rough equivalent in Linux to a shortcut in Windows) , then `which` will display the location of the link only; it will **not** follow the link to display the directory containing the actual binary in question.
{% endhint %}







