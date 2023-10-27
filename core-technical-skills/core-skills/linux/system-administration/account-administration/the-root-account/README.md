# The root Account

Every Linux system starts out with at least one administrative user account; the `root` user, and possibly one or more regular user accounts given a name that you choose, or a name assigned by your Linux distribution. In _**most**_ cases, you log in as a regular user and become the `root` user perform an administrative task.

The root user has complete control of the operation of your Linux system. That user can open any file or run any program. The root user also installs software packages and adds accounts for other people who use the system.

{% hint style="info" %}
If you are coming from a Windows background, it can be helpful to think of the `root` account as similar to the Administrator in Windows
{% endhint %}

When you first install most Linux systems (although not all systems), you add a password for the `root` user. You must remember and protect this password; you need it to log in as `root`, or to switch user to `root` while you are logged in as some other user.

### Exercise - Log In as root

To become familiar with the `root` user account, you can simply log in as the `root` user. I recommend trying this from a virtual console. To do so, press `Ctrl` + `Alt` + `F3`, then when you see the login prompt, type `root`, press `Enter`, and enter the password. A login session for `root` will open. When you are finished, type exit, and then press `Ctrl` + `Alt` + `F1` to return to the regular desktop login.

After you have logged in as `root`, the home directory for the root user is typically `/root`. The home directory, and other information associated with the `root` user account, are located in the `/etc/passwd` file.&#x20;

Here’s what the root entry looks like in the `/etc/passwd` file:

```
cat /etc/passwd | grep root
```

![The entry for the root account in /etc/passwd](<../../../../../../.gitbook/assets/image (159).png>)

This shows that for the user named `root`, the user ID is set to `0` (root user), the group ID is set to `0` (root group), the home directory is `/root`, and the shell for that user is `/bin/bash`.

You can change the home directory or the shell used by editing the values in this file. A better way to change these values, however, is to use the `usermod` command, which we will cover shortly.

At this point, any command that you run from your shell is run with root privilege. **So be careful**. You have much more power to change (and damage) the system than you did as a regular user. Type exit when you are finished. If you are on a virtual console and have a desktop interface running on another console, press `Ctrl` + `Alt` + `F1` to return to the graphical login screen if you are using a Linux desktop system.

{% hint style="info" %}
By default, the `root` account has no password set in Ubuntu. This means that even though the account exists, you cannot log in using it, or use `su` to become the root user. This adds an additional level of security to Ubuntu, and requires you to use `sudo` before each command that you want to execute as the root user
{% endhint %}
