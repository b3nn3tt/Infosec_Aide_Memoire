# Becoming root with su

If you're already logged in as a regular user and want to make a quick admin change, you don't have to go through the hassle of logging out and logging back in as **root**. This could also be the case if you're trying to get into a Linux system over the network, and it doesn't let root users log in remotely for security reasons.

That's where the **`su`** (Substitute User) command comes in handy. It lets you "switch over" to another user account on the fly if you know the password.

{% hint style="info" %}
Most of the time, **`su`** is used to swap to the root account from a standard user.
{% endhint %}

If you try to use `su` on a system where a password has not been set for **root** (typical in default Ubuntu installs), you will notice that you receive an authentication error:

![Ubuntu default installation, where root has no password set](<../../../../../../.gitbook/assets/image (164).png>)

You can overcome this by using the **`sudo`** command, assuming that the user you are logged in with is a member of the **`sudo`** group.&#x20;

{% hint style="info" %}
We will look at **`sudo`** more in depth next, but at this point all you need to recognise is that as a member of the **`sudo`** group, any commands you execute leveraging **`sudo`** will be executed with **root** privileges.&#x20;
{% endhint %}

Therefore, to authenticate as **root**, a **`sudo`** user can preface **`su`** with **`sudo`**, and when authenticating with their own password, the user will then become `root`:

![A user, as a member of the sudo group, is able to switch to the root account via sudo su](<../../../../../../.gitbook/assets/image (86).png>)

Using this type of configuration adds security to the use of the **root** account, and is considered best practice.

When the root account DOES have a password set, then using **su** is super simple:

```
su
```

When prompted, simply type the root user’s password. The prompt for the regular user (`$`) changes to the superuser prompt (`#`):

![Using su to become root](<../../../../../../.gitbook/assets/image (49).png>)

At this point, you have full permission to run any command and use any file on the system.

##

## su Limitation: root User Environment

one thing that the **`su`** command doesn’t do when used this way is read in the **root** user’s **environment**. As a result, you may type a command that you know is available and get the message **`Command Not Found`**.&#x20;

To fix this problem, use the **`su`** command with the dash (**`-`**) option instead like this:

```
su -
```

![Logging in as root via su, assuming the root user environment](<../../../../../../.gitbook/assets/image (81).png>)

You still need to type the password as before, but after that everything that normally happens at login for the **root** user happens after the **`su`** command is completed. Your current directory will be the **root** home directory - probably **`/root`**, and things such as the root user’s PATH variable are used. If you become the **root** user by just typing **`su`**, rather than **`su -`**, you don’t change directories or the environment of the current login session.

{% hint style="info" %}
When you use the **`su`** command with a username and the dash option, like **`su - john`**, you'll be logging in as the user named 'john', assuming you enter the correct password. This is quite handy for diagnosing issues that only affect a specific user's account, like trouble with printing documents or sending emails.



If you're already logged in as the root user and use the **`su`** command to switch to another user, you won't be prompted for a password because you have root privileges. For instance, if you're **root** and you type **`su - john`**, you'll switch to John's user without needing to enter his password. This is because, as **root**, you **have the authority to assume the identity of any user on the system**.



However, if you're logged in as a regular user and want to switch to another user account using **`su - username`**, you will need to enter the password for that user account. Failing to provide the correct password will result in a denial of access. This security measure ensures that only authorized users can access specific user accounts on the system.
{% endhint %}
