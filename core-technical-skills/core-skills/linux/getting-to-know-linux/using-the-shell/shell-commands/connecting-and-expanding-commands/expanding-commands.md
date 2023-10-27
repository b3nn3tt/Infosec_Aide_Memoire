# Expanding Commands

With command substitution, you essentially **let the shell handle a command's output** rather than the command itself. This nifty trick allows one command's output to be passed as an **argument** to another command. You've got two ways to do this:

1. `$(command)`&#x20;
2. `` `command` ``

{% hint style="info" %}
Just a heads up, those are **backticks** on the latter, <mark style="color:red;">**not your usual single quotes**</mark>.
{% endhint %}

In this approach, the command can have all the bells and whistles: options, metacharacters, and arguments. Here's an example of command substitution in action:

```
vi $(find /home | grep xyzzy)
```

In this example, the command substitution is done **before the** `vi` **command is run**. It runs as follows:

1. First, the `find` command starts at the `/home` directory and prints out all of the files and directories below that point in the filesystem
2. The output is piped to the `grep` command, which filters out all files except for those that include the string **xyzzy** in the filename
3. Finally, the `vi` command opens all filenames for editing (one at a time) that include **xyzzy**.

{% hint style="info" %}
If you run the above steps and are not familiar with vi, you can type `:q!` to exit the file.
{% endhint %}

This particular example is useful if you want to edit a file for which you know the name, but not the location. As long as the string is uncommon, you can find and open every instance of a filename existing beneath a point you choose in the filesystem.

In other words, <mark style="color:red;">**don’t use**</mark><mark style="color:red;">** **</mark><mark style="color:red;">**`grep`**</mark><mark style="color:red;">** **</mark><mark style="color:red;">**from the root filesystem or you’ll match and try to edit several thousand files**</mark>.

##

## Expanding Arithmetic Expressions

Occasionally, you might fancy passing some maths results over to a command. There are a couple of ways you can expand a mathematical expression and hand it over to the shell:

```
$[expression]
```

![Arithmetic expression is interpreted first, and passed to echo for printing to the terminal](<../../../../../../../.gitbook/assets/image (27).png>)

&#x20;   or

```
 $(expression)
```

![The result of the commands, once complete, is passed to echo for printing to ther](<../../../../../../../.gitbook/assets/image (21).png>)

##

## Expanding Variables

Variables that store information within the shell can be **expanded** using the dollar sign `$` metacharacter.

When you expand an environment variable on a command line, what you'll see printed is the variable's value, not its name, like this:

```
ls -l $HOME
```

![Using $HOME as an argument to ls -l causes a long listing of the home directory to be printed](<../../../../../../../.gitbook/assets/image (108).png>)

