# sudo

Particular users can be given administrative permissions for particular tasks, or any task for that matter, by typing `sudo` followed by the command they want to run. This allows said user to execute commands "as `root`" without the necessity for sharing the `root` password. The `sudoers` facility is the most common way to provide such privilege.

Using `sudoers` for any users or groups on the system, you can do the following:

* Assign `root` privilege for any command they run with `sudo`
* Assign `root` privilege for a select set of commands
* Give users `root` privilege without sharing the root password; users provide their own password to gain `root` privilege
* Allow users, if you choose, to run `sudo` without entering a password at all
* Track which users have run administrative commands on your system

{% hint style="info" %}
If a user leverages `su`, all you know is that someone with the `root` password logged in. Beyond this, oversight of their activities is limited. With the `sudo` command, logs are created to capture which user run an administrative command, providing a more verbose account of privileged user actions
{% endhint %}

With the `sudoers` facility, giving full or limited root privileges to any user simply entails adding the user to the `/etc/sudoers` file, and defining what privilege you want that user to have. Then, the user can run any command they have been granted privileges for by preceding said command with `sudo` .

For example, here we see a standard user trying to view the contents of the `/etc/shadow` file, and then again via `sudo`:

![Privileged Vs Un-Privileged execution](<../../../../../../../.gitbook/assets/image (193).png>)
