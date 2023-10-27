# Becoming root with su

Although you can become the superuser by logging in as `root`, sometimes that is not convenient. For example, you may be logged in to a regular user account and just want to make a quick administrative change to your system without having to log out and log back in. You may need to log in over the network to make a change to a Linux system, but find that the system doesn’t allow `root` users in from over the network - a common practice for secure Linux systems.

One solution is to use the `su` command. `su` stands for Substitute User, and it can be used to simply switch to any other user present on the system provided you know their credentials. It is, however, most commonly used to switch from a standard user to `root`.

If you try to use `su` on a system where a password has not been set for root (typical in default Ubuntu installs), you will notice that you receive an authentication error:

![Ubuntu default installation, where root has no password set](<../../../../../../.gitbook/assets/image (164).png>)

You can overcome this by using the `sudo` command, assuming that the user you are logged in with is a member of the `sudo` group. We will look at `sudo` more in depth later, but at this point all you need to recognise is that as a member of the `sudo` group, any commands you execute leveraging `sudo` will be executed with `root` privileges. Therefore, to authenticate as root, a `sudo` user can preface `su` with `sudo`, and when authenticating with their own password, the user will then become `root`:

![A user, as a member of the sudo group, is able to switch to the root account via sudo su](<../../../../../../.gitbook/assets/image (86).png>)

Using this type of configuration adds security to the use of the `root` account, and is considered best practice.

When the root account DOES have a password set, then the use of su is very simple:

```
su
```

When prompted, simply type the root user’s password. The prompt for the regular user (`$`) changes to the superuser prompt (`#`):

![Using su to become root](<../../../../../../.gitbook/assets/image (49).png>)

At this point, you have full permission to run any command and use any file on the system.

### root User Environment

one thing that the `su` command doesn’t do when used this way is read in the `root` user’s **environment**. As a result, you may type a command that you know is available and get the message `Command Not Found`.&#x20;

To fix this problem, use the `su` command with the dash (`-`) option instead like this:

```
su -
```

![Logging in as root via su, assuming the root user environment](<../../../../../../.gitbook/assets/image (81).png>)

You still need to type the password as before, but after that everything that normally happens at login for the `root` user happens after the `su` command is completed. Your current directory will be the `root` home directory - probably `/root`, and things such as the root user’s PATH variable are used. If you become the `root` user by just typing `su`, rather than `su -`, you don’t change directories or the environment of the current login session.

{% hint style="info" %}
If you add the name of a valid system user as a command argument, such as `su - john`, then you can log in as said system user (provided you have their credentials). This is useful for troubleshooting a problem that is being experienced by a particular user but not by others on the computer, such as an inability to print or send email.

If you were `root` user before you typed this command, then afterward you would have only the permissions to open files and run programs that are available to the user you just switched to. As the `root` user, after you type the `su` command to become another user, you don’t need a password to continue - after all, at the point you typed the command you were `root`.&#x20;

Conversely, if you type that command as a regular user, you must type the new user’s password, else you will fail authentication.
{% endhint %}
