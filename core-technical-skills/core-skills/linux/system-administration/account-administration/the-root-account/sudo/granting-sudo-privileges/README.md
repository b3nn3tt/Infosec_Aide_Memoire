# Granting sudo privileges

So, now we know what **`sudo`** is, it's time to configure some privileges. We can do this several ways, but by far the most common is to add a user to the already existent **`sudo`** group. We can achieve this with the **`usermod`** command. Alternatively, we can edit the **`/etc/sudoers`** file with **`visudo`**. In this section, we will explore both methods.



## usermod

Granting a new user complete sudo rights is a routine task. While you could fine-tune this within the **`visudo`** utility, using **`usermod`** is a simpler alternative. This approach does hinge on the existence of a group that's already configured with the required permissions. For this instance, we'll add a user to the default **`sudo`** group that's present on the majority of up-to-date systems.

To add a user to the sudo group, enter the following:

```
sudo usermod -aG sudo USERNAME
```

Breaking down the command options options:

* **`-aG`**: This option is actually two options used together.
  * **`-a`** or **`--append`**: This option tells **`usermod`** to add the user to the specified group without removing them from their current groups. Without this option, the user might be removed from any groups not listed in the command
  * **`-G`**: This specifies a list of supplementary groups which the user is also a member of. Here, it is followed by **`sudo`**, which is the group we're adding the user to

{% hint style="info" %}
Debian-like operating systems, such as Ubuntu, create the **`sudo`** group with purpose similar to that of another group known as **`wheel`** . The **`wheel`** group is a special user group used on some Unix systems, mostly BSD systems, to control access to the **`su`** or **`sudo`** command.
{% endhint %}



## visudo

The **`visudo`** command is essentially a safety tool for editing the **`/etc/sudoers`** file, which sets the rules for when the **`sudo`** command can be used for escalating privileges. When you run **`visudo`**, it opens the **`/etc/sudoers`** file in a text editor, but also performs checks to ensure that any changes made won't break the system's ability to use **`sudo`**.

Editing **`/etc/sudoers`** directly can be risky; a single syntax error could prevent **`sudo`** from functioning correctly. Therefore, **`visudo`** is the recommended method because it confirms the file's syntax is correct before saving any modifications. It also prevents the scenario where two people (or the same person in two different sessions) are editing the file at the same time, which could cause conflicts or errors.

{% hint style="info" %}
**`visudo`** typically uses the **`vi`** editor by default, but it can be configured to use another text editor like **`nano`**, which I much prefer for its simplicity. Changes to the sudoers file are usually small and precise, making a user-friendly editor like nano an appealing option for many Linux distributions.
{% endhint %}

### visudo Command Options

<table data-header-hidden><thead><tr><th width="209">Option</th><th>Description</th></tr></thead><tbody><tr><td><strong>Option</strong></td><td>Description</td></tr><tr><td><code>-c</code></td><td>Enable check-only mode. The existing <code>/etc/sudoers</code> file will be checked for syntax errors, owner and mode. A message will be printed to the standard output describing the status of <code>/etc/sudoers</code> unless the <code>-q</code> option was specified. If the check completes successfully, <code>visudo</code> will exit with a value of <code>0</code>. If an error is encountered, <code>visudo</code> will exit with a value of <code>1</code></td></tr><tr><td><code>-f sudoers</code></td><td>Specify an alternate <code>/etc/sudoers</code> file location. With this option, <code>visudo</code> will edit (or check) the<code>sudoers</code> file of your choice, instead of the default, <code>/etc/sudoers</code>. The lock file used is the specified <code>sudoers</code> file with "<code>.tmp</code>" appended to it. <br><br>In check-only mode only, the argument to <code>-f</code> may be <strong>-</strong>, indicating that <code>sudoers</code> will be read from the standard input</td></tr><tr><td><code>-h</code></td><td>The <code>-h</code> (help) option causes <code>visudo</code> to print a short help message to the standard output and exit</td></tr><tr><td><code>-q</code></td><td>Enable quiet mode. In this mode details about syntax errors are not printed. This option is only useful when combined with the <code>-c</code> option</td></tr><tr><td><code>-s</code></td><td>Enable strict checking of the <code>sudoers</code> file. If an alias is used before it is defined, <code>visudo</code> will consider this a parse error. Note that it is not possible to differentiate between an alias and a hostname or username that consists solely of uppercase letters, digits, and the underscore (<strong><code>_</code></strong>) character</td></tr><tr><td><code>-V</code></td><td>The <code>-V</code> (version) option causes <code>visudo</code> to print its version number and exit</td></tr></tbody></table>
