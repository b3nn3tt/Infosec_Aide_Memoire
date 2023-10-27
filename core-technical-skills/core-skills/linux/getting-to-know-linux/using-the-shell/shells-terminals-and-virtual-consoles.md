# Shells, Terminals, and Virtual Consoles

There are multiple ways in which we can interact with the shell in Linux. The three most common ways are:

* A Shell prompt
* Terminal window
* Virtual console

## The Shell Prompt

You will most commonly run into the Shell prompt if you are using a distribution with no graphical interface (or one where the GUI has been disabled). You will simply be presented with a text based command prompt, where you type in commands singularly:

![An example of a shell prompt from Fedora, installed with no GUI](<../../../../../.gitbook/assets/image (227).png>)

&#x20;The default prompt for a regular user is a dollar sign:

```
$
```

For the root user, the default prompt is the pound sign (`#`), which you might know as the number sign, or perhaps the hashtag:

```
#
```

{% hint style="info" %}
We'll delve into standard users and the root user in an upcoming section.
{% endhint %}

On the majority of Linux setups, the `$` and `#` prompts are placed after a string showing your current username, the name of the system, and the directory you're currently in. So, if the user **bennett** is having a session on a computer named **example** and is currently in the **/usr/share/** directory, it'd look a bit like this:

```
bennett@example:/usr/share$
```

##

## The Terminal Window

If your Linux system has a GUI installed, popping open a **Terminal Emulator** (often just called the Terminal Window, or even just the Terminal) to kick off a shell is pretty straightforward. Most times, you can:

* **Right-click the desktop**\
  Check out the dropdown menu that appears. If you spot options like Open in Terminal, Shells, New Terminal, Terminal Window, Xterm, or something along those lines, give it a click. Some versions of Linux might not have this option
*   **Click the panel menu**\
    A lot of Linux desktops have a **panel,** either at the top or bottom of your screen, acting as a handy launchpad for applications. On systems with the GNOME 2 desktop, for instance, you can navigate:

    \
    &#x20;   **Applications ➪ System Tools ➪ Terminal** \


    If you're on GNOME 3, hit the Activities menu, type in 'Terminal', and hit Enter.

Once you have the Terminal open, you interact with it in much the same way as you would the shell prompt:

![A terminal window spawned in the Ubuntu GUI](<../../../../../.gitbook/assets/image (153).png>)

##

## Virtual Consoles

In Linux distributions that feature a graphical desktop, you'll usually find that there are multiple virtual consoles ticking away in the background, ready and waiting for you to use. These virtual consoles let you have several shell sessions up and running alongside your graphical interface, all at the same time.

Switching between these virtual consoles is a breeze – just hold down `Ctrl` and `Alt`, and then tap one of the `F1` to `F6` function keys.&#x20;

To paint a picture, if you’re using Fedora, a combination of `Ctrl` + `Alt` + `F1` (or `F2`, `F3`, `F4`, and so on, right up to `F6`) will whisk you away to one of the available seven virtual consoles. You’ll find the graphical user interface usually hanging out on one of the first two virtual consoles, while the remaining five are where your text-based adventures unfold. And when you’re ready to head back to the GUI (and it’s up and running), a quick `Ctrl` + `Alt` + `F1` should do the trick!

{% hint style="info" %}
On some systems, the GUI may run on a different virtual console, such as Virtual Console 2 (`Ctrl` + `Alt` + `F2`).
{% endhint %}

### Try it yourself

1. Hold down the `Ctrl` + `Alt` keys and press `F3`. You should see a plain-text login prompt
2. Log in using your username and password. Try a few commands out
3. &#x20;When you are finished, type `exit` to exit the shell and then press `Ctrl` + `Alt` + `F1` or `Ctrl` + `Alt` + `F2` to return to your graphical desktop interface

You can go back and forth between these consoles as much as you like!!
