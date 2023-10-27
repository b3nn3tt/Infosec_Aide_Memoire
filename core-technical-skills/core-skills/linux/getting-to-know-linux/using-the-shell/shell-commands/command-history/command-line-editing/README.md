# Command Line Editing

## Command Line Editing

When you make a mistake in typing out a command, the bash shell's got you covered – you **don't need to erase everything and start from scratch**. You can also pull up a past command and tweak it to craft a new one.&#x20;

Out of the box, bash employs command-line editing inspired by the [emacs](https://www.gnu.org/software/emacs/) text editor. If you've had a play with emacs before, then many of the keystrokes mentioned here might be familiar to you.

{% hint style="info" %}
If you prefer [vi](https://en.wikipedia.org/wiki/Vi) for editing shell command lines, you can easily make that happen. Add the following line to the `.bashrc` file in your home directory:\
\
**set -o vi**\
\
From then on, every time you launch a shell, you'll be in familiar territory with those vi commands ready to edit!
{% endhint %}

To do the editing, you can use a combination of control keys, meta keys, and arrow keys. For example:

* `Ctrl` + `f` means to hold down the Ctrl key, and type f
* `Alt` + `f` means to hold down the Alt key, and type f

{% hint style="info" %}
Instead of the Alt key, your keyboard may use a Meta key or the Esc key. On a Windows keyboard, you can use the Windows key.
{% endhint %}



## Let's Give it a Try!

To try out a bit of command-line editing, enter the following command:

```bash
ls /usr/bin | sort -f | less
```

This command:

1. Lists the contents of the `/usr/bin` directory
2. Sorts the contents in alphabetical order (regardless of case)
3. Pipes the output to `less`

{% hint style="info" %}
The `less` command displays the first page of output, after which you can go through the rest of the output one line (press Enter) or one page (press spacebar) at a time. Simply press `q` when you are finished.
{% endhint %}

Now, let's change this command, altering `/usr/bin` to `/bin`. You can use the following steps to change the command:

**1. Press the up arrow (↑) key**\
This displays the most recent command from your shell history

**2. Press `Ctrl` + `a`**\
This moves the cursor to the beginning of the command line

**3. Press `Ctrl` + `f` or the right arrow (→) key**\
Repeat this command a few times to position the cursor under the first slash (/)

**4. Press `Ctrl` + `d`**\
Type this command four times to delete /usr from the line

**5. Press `Enter`**\
This executes the command line

When you're tweaking a command line, you can type regular characters at any point, with your new characters appearing at the location of your text cursor. You can use right → and left ← arrows to move the cursor from one end to the other on the command line.

You can also press the up ↑ and down ↓ arrow keys to step through your command history and select one for editing.
