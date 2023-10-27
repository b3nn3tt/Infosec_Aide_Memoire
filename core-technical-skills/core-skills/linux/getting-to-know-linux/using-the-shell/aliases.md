# Aliases

The `alias` command lets you whip up a quick shortcut for any command or set of options you might fancy using again in the future. To pop a new alias into the mix, or to have a look at existing ones, just use the `alias` command.&#x20;

Here are a few bash shell examples to show you how it's done:

```
alias p='pwd ; ls –CF'
alias rm='rm -i'
```

In the first example, the letter `p` is assigned to run the command `pwd` and then to run `ls -CF` to print the current working directory and list its contents in column form.&#x20;

The second example runs the `rm` command with the `-i` option each time you type `rm`. For those of you who are new to bash, `rm` is short for remove, so is used to <mark style="color:red;">delete files</mark>.

{% hint style="info" %}
This is an alias that is often set automatically for the **root** user (superuser). Instead of just removing files, you are prompted for each individual file removal. This prevents you from automatically removing all of the files in a directory by mistakenly typing something such as `rm *`.

We will look at the importance of the root user later on, but for now, know that the superuser can essentailly do ANYTHING, so telling `rm` to remove all files on the system will achieve just that, metaphorically nuking up your computer...
{% endhint %}

##

## Making an Alias Persistent

Note that adding an alias in the manner depicted earlier only persists for the current session. The moment you close that shell session down, your alias will die. If you want to render the change permanent, you need to follow modify your local `.bashrc` file:

```
nano ~/.bashrc
```

```
# ~/.bashrc: executed by bash(1) for non-login shells.

# Note: PS1 and umask are already set in /etc/profile. You should not
# need this unless you want different defaults for root.
# PS1='${debian_chroot:+($debian_chroot)}\h:\w\$ '
# umask 022

# You may uncomment the following lines if you want `ls' to be colorized:
# export LS_OPTIONS='--color=auto'
# eval "`dircolors`"
# alias ls='ls $LS_OPTIONS'
# alias ll='ls $LS_OPTIONS -l'
# alias l='ls $LS_OPTIONS -lA'
#
# Some more alias to avoid making mistakes:
# alias rm='rm -i'
# alias cp='cp -i'
# alias mv='mv -i'

alias ..='cd ..'
alias lsa='ls -la'
```

With the `.bashrc` file modified and saved, refresh the current shell session:

```
source ~/.bashrc
```

Now, every time you open a shell session, the contents of the `.bashrc` file are parsed, and the newly added aliases will take effect every time.

{% hint style="info" %}
In Linux, each user has their own home direcotry, usually located at `/home/username` within the file system. In the above command, we've used `~/` before `.bashrc`. This `~/` is a snappy way to refer to the current user's home directory.
{% endhint %}

##

## <mark style="color:red;">!!!CAUTION!!!</mark>

<mark style="color:red;">**The alias command does not have ANY restrictions on the words used for an alias.**</mark> This means you can set up an alias that shares its name with an already existing command. As discussed in the [Non-PATH Commands](shell-commands/non-path-commands.md) section, aliases take priority over other commands. Hence, if there's a naming overlap between an alias and a genuine command, the system will favour the alias, which could inadvertently block the real command from running.

Let's illustrate this with a hypothetical example:

```
alias mkdir='ping -c 1 localhost'
```

![An example where there is a name clash between a newly created alias and an existing command](<../../../../../.gitbook/assets/image (201).png>)

In this example, I've set up an alias named `mkdir`, coincidentally the same name as the genuine command for creating directories. Instead of its original function, our alias triggers the command `ping -c 1 localhost`, a command used for checking network connectivity. So, every time I input `mkdir`, rather than creating a new directory, the system will conduct a network ping.

Should a situation like this occur, the solution is simple. We can either exit the current shell session, or use the unalias command to unset the offending alias:

```
unalias mkdir
```

![Removing the offending alias, restoring normal functionality](<../../../../../.gitbook/assets/image (177).png>)

{% hint style="info" %}
The above solution assumes you haven't committed your alias to your **.bashrc** file.&#x20;

When you use the `unalias` command, it only removes the alias from your current session. If you've added the alias to your `.bashrc` file, you'll need to manually edit and remove it, or it will be reinstated the next time you open a new shell.
{% endhint %}
