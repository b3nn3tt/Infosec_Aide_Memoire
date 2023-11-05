# The root Account

Every Linux setup begins with the all-powerful **root** account – the top dog of user accounts. It's the admin with unrestricted access to everything on the system. This user can access any file, start up any program; basically anything goes. On top of that, the root account is in charge of key tasks like installing new software and creating user accounts for others who need to use the computer.

For day-to-day use, you'd ordinarily log in with a regular user account, one that's got your own chosen username or the one your Linux flavour has set up for you. Then, if you need to do something that needs admin powers, you switch hats and become the root user just for that task. It's a bit like having a regular key for the staff entrance and a master key for the entire building – you only use the master key when you really need to.

{% hint style="info" %}
If you are coming from a Windows background, it can be helpful to think of the **`root`** account as similar to the **Administrator** in Windows
{% endhint %}

When you first install most Linux systems (although not all systems), you add a password for the **root** user. You must remember and protect this password; you need it to log in as **root**, or to switch user to **root** while you are logged in as some other user.

###

## Exercise - Log In as root

To become familiar with the **root** user account, you can simply log in as the **root** user. I recommend trying this from a virtual console. To do so, press **`Ctrl`** + **`Alt`** + **`F3`**, then when you see the login prompt, type **`root`**, press **`Enter`**, and enter the password. A login session for **root** will open.

<mark style="color:red;">**At this point, any command that you run from your shell is run with root privilege. So be careful. You have much more power to change (and damage) the system than you did as a regular user.**</mark>

After you have logged in as **root**, the home directory for the root user is typically **`/root`**. The home directory, and other information associated with the **root** user account, are located in the **`/etc/passwd`** file.&#x20;

When you are finished, type **`exit`**, and then press **`Ctrl`** + **`Alt`** + **`F1`** to return to the regular desktop login.

Here’s what the root entry looks like in the **`/etc/passwd`** file:

```bash
cat /etc/passwd | grep root
```

![The entry for the root account in /etc/passwd](<../../../../../../.gitbook/assets/image (159).png>)

This shows that for the user named **root**, the user ID is set to **`0`** (root user), the group ID is set to **`0`** (root group), the home directory is **`/root`**, and the shell for that user is **`/bin/bash`**.

You can change the home directory or the shell used by editing the values in this file. A better way to change these values, however, is to use the **`usermod`** command, which we will cover shortly.

{% hint style="info" %}
By default, the **root** account has no password set in Ubuntu. This means that even though the account exists, you cannot log in using it, or use **`su`** to become the root user. This adds an additional level of security to Ubuntu, and requires you to use **`sudo`** before each command that you want to execute as the root user
{% endhint %}
