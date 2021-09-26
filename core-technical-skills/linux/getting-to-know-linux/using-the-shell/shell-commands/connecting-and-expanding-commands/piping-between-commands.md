# Piping Between Commands

The pipe `|` metacharacter connects the output from one command to the input of another command. This lets you have one command work on some data and then have the next command deal with the results. Here is an example of a command line that includes pipes:

```text
cat /etc/passwd | sort | less
```

This command lists the contents of the `/etc/passwd` file, and pipes the output to the sort command, which organises alphabetically the usernames that begin each line of the `/etc/passwd` file, and pipes the output to the less command \(to page through the output\).

Pipes are an excellent illustration of how UNIX, the predecessor of Linux, was created as an operating system made up of building blocks. A standard practice in UNIX was to connect utilities in different ways to get different jobs done.

For example, before the days of graphical word processors, users created plain-text files that included macros to indicate formatting. To see how the document really appeared, they would use a command such as the following:

```text
gunzip < /usr/share/man/man1/grep.1.gz | nroff -c -man | less
```

In this example, the contents of the `grep` man page \(grep.1.gz\) are directed to the `gunzip` command to be unzipped. The output from `gunzip` is piped to the `nroff` command to format the man page using the manual macro \(-man\). To display the output, it is piped to the `less` command. Because the file being displayed is in plain text, you could have substituted any number of options to work with the text before displaying it. You could sort the contents, change or delete some of the content, or bring in text from other documents.

The key to all of this is that, instead of all of those features being in one program, you get results from piping and redirecting input and output between multiple commands.

