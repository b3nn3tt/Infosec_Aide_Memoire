# Non-PATH Commands

Not all of the commands you run are located in directories in your PATH variable. Some commands are actually built into the shell. 

Other commands can be overridden by creating "_aliases_" that define any commands and options that you want said command to run. There are also ways of defining a function that consists of a stored series of commands.

Here is the order in which the shell checks for the commands you type:

## 1. Aliases

These are names set by the `alias` command that represent a particular command and a set of options. Type `alias` to see what aliases are set in your current session:

```text
alias
```

![Some examples of configured aliases in Ubuntu](../../../../../.gitbook/assets/image%20%2828%29.png)

Often, aliases enable you to define a short name for a long, complicated command. We will look at how to create an alias later in the section.

## 2. Shell Reserved Word

These are words reserved by the shell for special use. Many of these are words that you would use in programming-type functions, such as `do`, `while`, `case`, and `else`.

## 3. Functions

This is a set of commands that is executed together within the current shell.

## 4. Built-In Commands

This is a command that is built-in to the shell. As a result, there is no representation of the command anywhere in the filesystem. Some of the most common commands that you will use are shell built-in commands, such as:

| Command | Description |
| :--- | :--- |
| `cd` | Used to change directories |
| `echo` | Outputs text to the screen |
| `exit` | Used to exit from the shell |
| `fg` | Bring a command running in the background to the foreground |
| `history` | Display a list of previously run commands |
| `pwd` | Display the current working directory |
| `set` | Set shell options |
| `type` | Used to find out the information about a Linux command, including its location |

## 5. Filesystem Command

This command is stored in, and executed from, the computer’s filesystem. In other words, they are the commands that are indicated by the value of the PATH variable. 

To determine the location of a particular command, you can use the type command. If you are using a shell other than bash, use the `which` command instead. For example, to find out where the bash shell command is located, enter the following:

```text
type bash
```

![An example of the type command](../../../../../.gitbook/assets/image%20%2819%29.png)

If a command resides in several locations, you can add the **-a** option to have all of the known locations of the command printed. For example, the command `type -a ls` should show an aliased and filesystem location for the ls command:

```text
type -a ls
```

![An example of the type command listing multiple locations](../../../../../.gitbook/assets/image%20%2818%29.png)

If a command is not in your PATH variable, you can use the `locate` command to try to find it. Using `locate`, you can search any part of the system that is accessible to you \(Some files are only accessible to the root user\).

