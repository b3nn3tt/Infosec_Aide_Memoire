# Aliases

Using the alias command, you can effectively create a shortcut to any command and options that you want to run later. You can add and list aliases with the alias command. Consider the following examples of using alias from a bash shell:

```text
alias p='pwd ; ls –CF'
alias rm='rm -i'
```

In the first example, the letter `p` is assigned to run the command `pwd` and then to run `ls -CF` to print the current working directory and list its contents in column form. 

The second example runs the `rm` command with the `-i` option each time you type `rm`. This is an alias that is often set automatically for the root user. Instead of just removing files, you are prompted for each individual file removal. This prevents you from automatically removing all of the files in a directory by mistakenly typing something such as `rm *`.

## Making an Alias Persistent

Note that adding an alias in the manner depicted earlier only persists for the current session. If you want to effect permanent change, you need to follow modify your local `.bashrc` file:

```text
nano ~/.bashrc
```

```text
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

```text
source ~/.bashrc
```

Now, every time you open a shell session, the contents of the `.bashrc` file are parsed, and the newly added aliases will take effect every time.

## !!!CAUTION!!!

The alias command does not have any restrictions on the words used for an alias. Therefore, it is possible to create an alias using a word that already corresponds to an existing command. We can see this in the following, rather arbitrary example:

```text
alias mkdir='ping -c 1 localhost'
```

![An example where there is a name clash between a newly created alias and an existing command](../../../../.gitbook/assets/image%20%287%29.png)

Should a situation like this occur, the solution is simple. We can either exit the current shell session, or use the unalias command to unset the offending alias:

```text
unalias mkdir
```

![Removing the offending alias, restoring normal functionality](../../../../.gitbook/assets/image%20%2810%29.png)









