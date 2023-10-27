# Using vim and vi to Edit Text Files

It’s almost impossible to use Linux for any period of time and not need a text editor because, as noted earlier, most Linux configuration files are plain-text files that you will almost certainly need to manually change at some point. If you are using a [GNOME](https://www.gnome.org/) desktop, you can run `gedit` (type _gedit_ into the Search box and press Enter, or select Applications ➪ Accessories ➪ gedit), which is fairly intuitive for editing text in a GUI.

You can also run a simple text editor called `nano` from the shell. It is true that `nano` isn't as feature rich as some other editors, but it is **very** user friendly, and often enough to get the job done. That being said, most Linux shell users use either the `vi` or the also popular `emacs` command to edit text files.

The advantage of vi over a graphical editor is that you can use the command from pretty much any shell, character terminal, or character-based connection over a network (leveraging network applications such as `telnet` or `ssh`, for example) — no graphical interface is required.

{% hint style="info" %}
99.9% of Linux systems you will come into contact with will have `vi` installed.
{% endhint %}

The following sections provide a brief tutorial on the `vi` text editor, which you can use to manually edit a text file from any shell. It also describes the improved versions of `vi`, called `vim`. The `vi` editor is somewhat difficult to learn at first, owing to its peculiar interaction contexts and key combinations, but after you become familiar with it, you never again have to use a mouse or a function key — you can edit and move around quickly and efficiently within files just by using the keyboard.&#x20;

Lovely stuff!
