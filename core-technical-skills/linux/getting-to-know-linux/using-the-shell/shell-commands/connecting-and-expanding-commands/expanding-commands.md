# Expanding Commands

With command substitution, you can have _**the output of a command interpreted by the shell instead of by the command itself**_. In this way, you can have the standard output of a command become an argument for another command. The two forms of command substitution are **$(command)** and **\`command\`** - Note that they are **backticks, not single quotes**.

The command in this case can include options, metacharacters, and arguments. The following is an example of using command substitution:

```
vi $(find /home | grep xyzzy)
```

In this example, the command substitution is done before the vi command is run. It runs as follows:

1. First, the `find` command starts at the `/home` directory and prints out all of the files and directories below that point in the filesystem
2. The output is piped to the `grep` command, which filters out all files except for those that include the string "**xyzzy"** in the filename
3. Finally, the `vi` command opens all filenames for editing (one at a time) that include xyzzy.

{% hint style="info" %}
If you run the above steps and are not familiar with vi, you can type `:q!` to exit the file.
{% endhint %}

This particular example is useful if you want to edit a file for which you know the name but not the location. As long as the string is uncommon, you can find and open every instance of a filename existing beneath a point you choose in the filesystem. In other words, _**don’t use grep from the root filesystem or you’ll match and try to edit several thousand files**_.

## Expanding Arithmetic Expressions

Sometimes, you want to pass arithmetic results to a command. There are two forms that you can use to expand an arithmetic expression and pass it to the shell:

```
$[expression]
```

![Arithmetic expression is interpreted first, and passed to echo for printing to the terminal](<../../../../../../.gitbook/assets/image (9).png>)

&#x20;   or

```
 $(expression)
```

![The result of the commands, once complete, is passed to echo for printing to ther](<../../../../../../.gitbook/assets/image (25).png>)

## Expanding Variables

Variables that store information within the shell can be expanded using the dollar sign `$` metacharacter.\
When you expand an environment variable on a command line, the value of the variable is printed instead of the variable name itself, as follows:

```
ls -l $HOME
```

![Using $HOME as an argument to ls -l causes a long listing of the home directory to be printed](<../../../../../../.gitbook/assets/image (11).png>)

