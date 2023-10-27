# Piping Between Commands

The pipe metacharacter, `|`, serves as a conduit, channeling the output of one command directly into the awaiting input of another. This seamless relay enables a succession of commands to collaboratively process data. Confused? Don't be - it's actually really easy.&#x20;

Let's see an example that stitches together commands using pipes:

```
cat /etc/passwd | sort | less
```

This command:

1. Prints the contents of the `/etc/passwd` file to the terminal
2. Pipes the output to the `sort` command, which arranges the entries alphabetically based on the usernames leading each line
3. Pipes the output to the `less` command, making it easier to browse through and navigate the output

Pipes perfectly embody the foundational ethos of UNIX, from which Linux evolved. At its heart, UNIX was envisaged as an operating system of interconnected building blocks. The principle was to cleverly chain these utilities together to handle a multitude of tasks.

Casting our minds back to the days before graphical word processors (sadly yes, I can remember those...), users penned plain-text files peppered with macros for formatting cues. To catch a preview of the document's actual appearance, they'd conjure up commands similar to:

```
gunzip < /usr/share/man/man1/grep.1.gz | nroff -c -man | less
```

Let's look more closely at what is happening here:

1. The contents of the `grep` **man page** (`grep.1.gz`) are handed over to `gunzip` for decompression
2. `nroff` steps in to format the page using the manual macro (hence, `-man`)
3. For a tidy presentation, we send it through `less`

Given it's all in plain text, there's a bunch of flexibility here. You could sort the content, adjust parts, or even integrate text from another document.

{% hint style="info" %}
A few points to zone in on...

1. **man pages** are like user **manuals** for computer commands, explaining what they do and how to use them
2. We asked `gunzip` to unpack the `grep.1.gz` file using a method called **redirection**. Essentially, we fed the file mentioned after the `<` symbol into `gunzip`. We'll dive deeper into this concept a bit later
3. Note that we used two pipes (`|`) - practically speaking, you can chain together as many commands using pipes as you want, or at least until you hit system limits like memory or CPU constraints. Just beware of complexity...
{% endhint %}

The standout point? Instead of relying on a single, hefty program, we achieve our goal by seamlessly chaining commands together, with piping and redirection being the stars of the show.
