# Command Line Editing

## Command Line Editing

If you type something wrong on a command line, the bash shell ensures that you don’t have to delete the entire line and start over. Likewise, you can recall a previous command line and change the elements to make a new command.&#x20;

By default, the bash shell uses command-line editing that is based on the [emacs](https://www.gnu.org/software/emacs/) text editor. If you are familiar with emacs, you probably already know most of the keystrokes described here...

{% hint style="info" %}
If you prefer the vi command for editing shell command lines, you can easily make that happen. Add the following line to the `.bashrc` file in your home directory:\
\
**set -o vi**\
\
The next time you open a shell, you can use vi commands to edit your command lines.
{% endhint %}

To do the editing, you can use a combination of control keys, meta keys, and arrow keys. For example:

* `Ctrl` + `f` means to hold down the Ctrl key, and type f
* `Alt` + `f` means to hold down the Alt key, and type f. \
  _Instead of the Alt key, your keyboard may use a Meta key or the Esc key. On a Windows keyboard, you can use the Windows key._

To try out a bit of command-line editing, enter the following command:

```
ls /usr/bin | sort -f | less
```

This command lists the contents of the `/usr/bin` directory, sorts the contents in alphabetical order (regardless of case), and pipes the output to `less`. The `less` command displays the first page of output, after which you can go through the rest of the output a line (press Enter) or a page (press spacebar) at a time. Simply press `q` when you are finished.

Now, let's change this command, altering `/usr/bin` to `/bin`. You can use the following steps to change the command:

&#x20;**1. Press the up arrow (↑) key**\
&#x20;This displays the most recent command from your shell history.\
\
&#x20;**2. Press `Ctrl` + `a`**\
&#x20;This moves the cursor to the beginning of the command line.\
\
&#x20;**3. Press `Ctrl` + `f` or the right arrow (→) key**\
&#x20;Repeat this command a few times to position the cursor under the first slash (/).\
\
&#x20;**4. Press `Ctrl` + `d`**\
&#x20;Type this command four times to delete /usr from the line.\
\
&#x20;**5. Press `Enter`**\
&#x20;This executes the command line

As you edit a command line, at any point you can type regular characters to add those characters to the command line. The characters appear at the location of your text cursor. You can use right → and left ← arrows to move the cursor from one end to the other on the command line.

You can also press the up ↑ and down ↓ arrow keys to step through previous commands in the history list to select a command line for editing.
