# Shell Commands

The simplest way to run a command is to simply type the name of the command from a shell. Commands are themselves small programs that the shell "_calls_" when you type its name - this is called command execution.

Commands, for the most part, have a similar syntax that it generally goes like this:

```text
[command name] [option] [argument]
```

Rather than endlessly list commands here, I will simply reference them and explain them as we go through the various sections. Instead, in this section we will focus on command management.

## PATH

So far you have typed out a few commands, such as `cat`, `grep`, and `chsh`, and you may be wondering "_where are those commands coming from?_", or "_how does the shell find the commands you type?_". The answer is that the shell will look to something that is called the **PATH**.

The idea is pretty simple; the **PATH** is a list of directories contained within the file system. When you type the name of a command, the shell will look in those directories, and if the command is found, it executes. So naturally, the first question is usually "_What's in the PATH?_". The directories that make up PATH are stored in a shell environment variable, in much the same way as the current running shell, and can be viewed in much the same way:

```text
echo $PATH
```

![An example of the contents of the $PATH variable](../../../../../.gitbook/assets/image%20%286%29.png)

As you can see, a list of directories is displayed, each separated by a colon. **The path directory order is important**. Directories are checked from left to right. So, in the above example, if there are two different programs that share the name `foo` where the first is located in `/usr/local/sbin` and the second in `/bin` . When the `foo` command is called, the one in `/usr/local/sbin` is executed as it appears earlier in the list.

    "_But what if I want to execute `foo` from `/bin` rather than from `/usr/local/sbin?`_"...

To overcome the natural behaviour of the shell, you can specify the exact location of the command you wish to execute by typing out the full location - this is known properly as the **Absolute Path**:

```text
/bin/foo
```

Alternatively, you can modify the order of the $PATH variable to ensure the correct program is called by the shell.

{% hint style="info" %}
**Unlike some other operating systems, Linux does not, by default, check the current directory for an executable before searching the PATH. It immediately begins searching the path, and executables in the current directory are run only if they are in the PATH variable, or you give their absolute \(such as `/home/user/scriptx.sh`\) or relative \(for example `./scriptx.sh`\) location. We will revisit the concept of Absolute and Relative PATH's a little later...**
{% endhint %}

## Locate Commands in PATH with `which`

To determine which directory in the PATH that a given command resides, you can use the `which` command:

```text
which COMMAND
```

![Example of the which command](../../../../../.gitbook/assets/image%20%2823%29.png)

{% hint style="info" %}
When you execute the `which` command, it will look in each directory specified in PATH for any binary file that has a corresponding name. However, if there is a "**Symbolic Link**" to a binary \(the rough equivalent in Linux to a shortcut in Windows\) , then `which` will display the location of the link only; it will **not** follow the link to display the directory containing the actual binary in question.
{% endhint %}









