# Choose your Shell

In most cases \(_see the note below_\), your default shell is the `bash` shell. You can change this if you wish, or you can launch into a different shell session from your current one.

{% hint style="info" %}
As stated earlier, some Linux distributions are moving away from `bash`, and adopting `zsh` as their default shell. Apple has also made the same decision.
{% endhint %}

## Enumerate the Default Shell

Each account can be configured to use a specific shell. It is quite common for different accounts to use different shells, based on their requirements. So, before doing anything else, it's wise to determine what shell the current user is running.

The easiest way to determine the current shell is by executing the following command:

```text
echo $SHELL
```

This will display the contents of the `$SHELL` environment variable, which will display the shell the current user is running.

What if you want to enumerate the shell configuration for other system accounts? You can inspect the `/etc/passwd` file, which contains the details of all system accounts:

```text
cat /etc/passwd
```

![Viewing the contents of /etc/passwd](../../../../.gitbook/assets/image%20%284%29.png)

We will circle back to the `/etc/passwd` file later, but for now you can see that at the end of each line, there is a value which determines which shell an account will use. Note that in some cases, entries like `nologin` or `/bin/false` indicate that the account in question does not use a shell - such accounts are non-interactive, and usually exist for system purposes rather than for human interaction.

If you happen to know the name of the account you wish to query, you can always filter the output of the earlier command to only return details you are interested in. To do this, we use the `grep` command:

```text
cat /etc/passwd | grep USERNAME
```

We will circle back around to the proper use of `grep` later, but this can often be a quick win.

## Open a New Shell

To try a different shell, simply type the name of that shell. Examples include:

* `ksh`
* `tcsh`
* `csh`
* `sh`
* `dash`

There are other shells you can choose from, assuming that they are installed on the system. You can display them with the following command:

```text
cat /etc/shells
```

![A list of selectable shells in Kali Linux](../../../../.gitbook/assets/image%20%2830%29.png)

You can try a few commands in your shell of choice, then simply type `exit` when you are finished to return to the previous shell.

## Configure a New Default Shell

The following command, if launched as an administrator, or via `sudo` \(more on this later...\) will allow you to change the default shell of a specified user:

```text
usermod --shell /bin/sh USERNAME
```

    or

```text
chsh --shell /bin/sh USERNAME
```

Either of these will set the default shell to be /bin/sh for the user you specify.

{% hint style="info" %}
Whilst it is **not recommended**, you could manually edit the `/etc/passwd` file with a text editor, but this invites complication if your edit goes sour.
{% endhint %}





