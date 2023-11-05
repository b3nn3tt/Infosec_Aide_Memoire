# sudo

The **`sudo`** command is a powerful tool that offers a more controlled method of granting administrative privileges to regular users without sharing the root password. When using **`sudo`**, a user can execute commands with **root-level privileges** while their actions are logged, which provides an audit trail of who did what.

In contrast to **`su`**, which switches your session to the root user, **`sudo`** executes a single trailing command with elevated privileges. This allows for a more granular level of access control, as you can configure exactly which commands each user is allowed to run as root or any other user. The **`sudoers`** facility is the most common way to provide such privilege.

Using **`sudoers`** for any users or groups on the system, you can do the following:

* Assign **root** privilege for any command they run with **`sudo`**
* Assign **root** privilege for a select set of commands
* Give users **root** privilege without sharing the root password; users provide their own password to gain **`root`** privilege
* Allow users, if you choose, to run **`sudo`** without entering a password at all
* <mark style="color:green;">**Track which users have run administrative commands on your system**</mark>

{% hint style="info" %}
If a user leverages **`su`**, all you know is that someone with the **root** password logged in. Beyond this, <mark style="color:red;">**oversight of their activities is limited**</mark>. With the **`sudo`** command, logs are created to capture which user run an administrative command, providing a more verbose account of privileged user actions
{% endhint %}



With the **`sudoers`** facility, giving full or limited **root** privileges to any user simply entails adding the user to the **`/etc/sudoers`** file, and defining what privilege you want that user to have. Then, the user can run any command they have been granted privileges for by preceding said command with **`sudo`** .

For example, here we see a standard user trying to view the contents of the **`/etc/shadow`** file, and then again via **`sudo`**:

![Privileged Vs Un-Privileged execution](<../../../../../../../.gitbook/assets/image (193).png>)
