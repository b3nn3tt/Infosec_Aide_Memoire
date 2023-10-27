# Choose your Shell

In most cases today, your "go-to" shell will likely be the bash shell. Of course, you've got the freedom to switch it up if that tickles your fancy, or simply hop into another shell session from where you are now.

{% hint style="info" %}
As we touched on earlier, there's a trend happening where some Linux distributions are gravitating towards `zsh`, giving bash a bit of a sidestep. Apple have made this call within MacOS.
{% endhint %}

##

## Discover the Default Shell

Each user account can be set up to run a particular shell. It's pretty normal for different user accounts to be rocking different shells, all depending on what they need. So, a smart move before diving in is to figure out which shell you're currently using.

The easiest way to determine the current shell is by executing the following command:

```
echo $SHELL
```

This will display the contents of the `$SHELL` **environment variable**, which will display the shell the current user is running.

{% hint style="info" %}
We will examine shell variables more closely a little later.
{% endhint %}

What if you want to find out, or **enumerate**, the shell configuration for other system accounts? You can display the contents of the `/etc/passwd` file with the `cat` command:

```
cat /etc/passwd
```

![Viewing the contents of /etc/passwd](<../../../../../.gitbook/assets/image (133).png>)

We'll revisit the `/etc/passwd` file a bit later on. But at a quick glance, you might've noticed that at the end of each line there's a bit that tells you which shell each account is set to use.

{% hint style="info" %}
If you come across entries like `nologin` or `/bin/false`, that's a hint that the account doesn't use an interactive shell. These accounts aren't intended for human use; they're non-interactive and mainly there to keep the system ticking along.
{% endhint %}

The `cat` command (short for **concatenate**), displays the contents of the file you direct it towards on the terminal. For instance, when we pointed it at `/etc/passwd`, it promptly laid out its content on our screen. However, if you're specifically interested in a particular account, sifting through the entire file using `cat` might seem inefficient. There are more precise methods to extract the information you need.

There's a handy way to filter the output of our `cat` command. Enter stage left: the `grep` command.

`grep` is a handy command-line tool that lets you **filter** for specific patterns or text within files, showing you the lines where they pop up. There are several ways to use grep which we will explore in later sections, but in this example, we will use a feature of the shell known as **piping** - a posh way of saying "take the output from one command and use it as input for another". We will use `cat` to print the contents of `/etc/passwd` to the terminal, "pipe" it (`|`) into the `grep` command, and filter the output for a given username:

```
cat /etc/passwd | grep USERNAME
```

The above command will result in output that matches our search term. So, if you wanted to list all of the accounts that are configured to use `/bin/noshell`, you would enter:

```
cat /etc/passwd | grep /bin/noshell
```

##

## Open a New Shell

To try a different shell, simply type the name of that shell. Examples include:

* `ksh`
* `tcsh`
* `csh`
* `sh`
* `dash`

There are other shells you can choose from, assuming that they are installed on the system. You can display them with the following command:

```
cat /etc/shells
```

![A list of selectable shells in Kali Linux](<../../../../../.gitbook/assets/image (173).png>)

You can try a few commands in your shell of choice, then simply type `exit` when you are finished to return to the previous shell.

{% hint style="info" %}
Different shells come with their own set of bells and whistles. It's worth having a look around to see what each one offers. As you get more comfy with Linux, you might find you'll prefer one shell for certain tasks, and another for something else entirely.

Give it a bash... (sorry)
{% endhint %}



## Configure a New Default Shell

The following command, if launched as an administrator, or via `sudo` (more on this later...) will allow you to change the default shell of a specified user:

```
usermod --shell /bin/sh USERNAME
```

&#x20;   or

```
chsh --shell /bin/sh USERNAME
```

Either of these will set the default shell to be `/bin/sh` for the user you specify.

{% hint style="info" %}
Whilst it is **not recommended**, you could manually edit the `/etc/passwd` file with a text editor, but this invites complication if your edit goes sour.
{% endhint %}
