# Shells, Terminals, and Virtual Consoles

There are several ways interact with the shell in Linux. The three most common ways are:

* A Shell prompt
* Terminal window
* Virtual console

## The Shell Prompt

You will most commonly run into the Shell prompt if you are using a distribution with no graphical interface \(or one where the GUI has been disabled\). You will simply be presented with a text based command prompt, where you type in commands singularly:

![An example of a shell prompt from Fedora, installed with no GUI](../../../../.gitbook/assets/image%20%2824%29.png)

 The default prompt for a regular user is simply a dollar sign:

```text
$
```

The default prompt for the root user is a pound sign \(also called a number sign or a hash tag\):

```text
#
```

In most Linux systems, the `$` and `#` prompts are preceded by your username, system name, and current directory name. For example, a login prompt for the user named `bennett` on a computer named `example` with `/usr/share/` as the current working directory would appear as follows:

```text
[bennett@example share]$
```

## The Terminal Window

If you are running a distribution that has the GUI enabled, you can open a **Terminal Emulator** \(usually referred to as the Terminal Window, or simply as the Terminal\) to spawn a shell. Most distributions make this a very simple task. You can usually either:

*  **Right-click the desktop** In the context menu that appears, if you see Open in Terminal, Shells, New Terminal, Terminal Window, Xterm, or some similar item, select it to start a Terminal window. \(Some distributions have disabled this feature.\)
* **Click the panel menu** Many Linux desktops include a panel at the top or bottom of the screen from which you can launch applications. For example, in some systems that use the GNOME 2 desktop, you can select:      **Applications ➪ System Tools ➪ Terminal**   To open a Terminal window. In GNOME 3, click the Activities menu, type Terminal, and press Enter.

One you have the Terminal open, you can interact with it in much the same way as you would the shell prompt.

![A terminal window spawned in the Ubuntu GUI](../../../../.gitbook/assets/image%20%2832%29.png)

## Virtual Consoles

More often than not, Linux distributions that include a graphical desktop start multiple virtual consoles running on the system. Virtual consoles are a way to have multiple shell sessions open at once, in addition to the graphical interface you are using. 

You can switch between virtual consoles by holding the `Ctrl` and `Alt` keys, and pressing a function key between `F1` and `F6`.

For example, in Fedora, press `Ctrl` + `Alt` + `F1` \(or F2, F3, F4,and so on up to F6 on most Linux systems\) to display one of seven virtual consoles. The GUI is typically located on one of the first two virtual consoles, and the other six virtual consoles are typically text-based virtual consoles. You can return to the GUI \(if one is running\) by pressing Ctrl+Alt+F1. 

{% hint style="info" %}
On some systems, the GUI may run on a different virtual console, such as Virtual Console 2 \(`Ctrl` + `Alt` + `F2`\).
{% endhint %}

### Try it yourself

1.  Hold down the `Ctrl` + `Alt` keys and press `F3`. You should see a plain-text login prompt
2. Log in using your username and password. Try a few commands out
3.  When you are finished, type `exit` to exit the shell and then press `Ctrl` + `Alt` + `F1` or `Ctrl` + `Alt` + `F2` to return to your graphical desktop interface

You can go back and forth between these consoles as much as you like!!

