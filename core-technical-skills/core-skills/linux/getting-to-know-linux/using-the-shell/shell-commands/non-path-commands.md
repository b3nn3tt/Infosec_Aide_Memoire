# Non-PATH Commands

While many of the commands you execute are binaries situated in the LFS and pointed to by the PATH variable, some commands are inherently integrated into the shell itself.

Other commands can be overridden by creating **aliases** that define commands and any options that you want said command to run. There are also ways of defining a **function** that consists of a stored series of commands.

When you input a command, the shell follows a specific sequence to determine its execution, which we'll examine in order of precedence.



## 1. Aliases

Aliases are custom shortcuts created using the `alias` command, representing a specific command combined with certain options. To view the active aliases in your ongoing session, simply type `alias`:

```
alias
```

![Some examples of configured aliases in Ubuntu](<../../../../../../.gitbook/assets/image (35).png>)

Often, aliases enable you to define a short name for a long, complicated command. I leverage aliases a lot in my day to day work, which i'll cover as they naturally crop up throughout my ramblings.



## 2. Shell Reserved Word

Reserved words in the shell are a bit like VIPs – they've got their own special roles. Think of terms like `do`, `while`, `case`, and `else`. They pop up in scripting a lot, helping with loops, making decisions, and directing the flow of actions. It's a good thing to remember not to use them as names for your own stuff, so everything keeps running smoothly!

{% hint style="info" %}
If you try to create an alias or a binary that shares the name of a reserved word, it can lead to a "**name collision**" or "**namespace collision**". In the context of shell scripting and command-line interactions, such a collision can cause confusion for the shell, potentially leading to unexpected behavior.&#x20;



It's always recommended to choose unique names for aliases, binaries, and functions to avoid overlapping with reserved words or other existing commands.
{% endhint %}





## 3. Functions

Functions are like little command bundles you create right in your shell. They group together a series of commands that get executed in tandem within the current shell environment. Think of them as your own custom-made shortcuts to carry out a string of actions without typing them all out each time.&#x20;

They become far more important when you start scripting, so we'll revisit these later on.



## 4. Built-In Commands

Built-in commands are essentially part and parcel of the shell itself. This means they don't live anywhere specific on the LFS – they're kind of like the shell's built-in toolset. A lot of the commands you'll frequently bump into and use are, in fact, these handy built-ins. Some examples include:

| Command   | Description                                                                    |
| --------- | ------------------------------------------------------------------------------ |
| `cd`      | Used to change directories                                                     |
| `echo`    | Outputs text to the screen                                                     |
| `exit`    | Used to exit from the shell                                                    |
| `fg`      | Bring a command running in the background to the foreground                    |
| `history` | Display a list of previously run commands                                      |
| `pwd`     | Display the current working directory                                          |
| `set`     | Set shell options                                                              |
| `type`    | Used to find out the information about a Linux command, including its location |

Again, rather than diving into a tonne of examples right now, I'll walk you through their uses as we stumble upon them.



## 5. Filesystem Command

These commands live right in your computer's filesystem. They're the ones that the PATH variable points to that we were looking at a little while ago.&#x20;

Wondering where a specific command hangs out? Just use the `type` command.

For instance, if you're curious about where the bash shell command is tucked away, give this a go:

```
type bash
```

![An example of the type command](<../../../../../../.gitbook/assets/image (167).png>)

If a command resides in several locations, you can add the **-a** option to have all of the known locations of the command printed. For example, the command `type -a ls` should show an aliased and filesystem location for the ls command:

```
type -a ls
```

![An example of the type command listing multiple locations](<../../../../../../.gitbook/assets/image (210).png>)

{% hint style="info" %}
If you're working in a shell that isn't bash, go for the `which` command.
{% endhint %}

If a command is not in your PATH variable, you can use the `locate` command to try to find it. Using `locate`, you can search any part of the system that is accessible to you (some files are only accessible to the root user).
