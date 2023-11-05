# visudo Guidance

I've put together this page to throw you some tips and examples for getting to grips with **`visudo`**. It's not the full monty, but it'll set you on the right path.



## Grant a Specific User FULL ROOT PRIVILEGES

Add the following USER Privilege Line to grant a specified user **`sudo`** provileges on all commands:

```
USER    ALL=(ALL:ALL) ALL
```



## Remove Password Requirement

Find the line belonging to the user or group you wish to remove the password requirement from, and add **`NOPASSWD`** in the following position:

```
USER    ALL=(ALL:ALL) NOPASSWD:ALL
```

{% hint style="info" %}
&#x20;`NOPASSWD` is a “tag” that means no password will be requested.
{% endhint %}

In the above example, we grant the user access to ALL commands via sudo without a password. It's a bit of an open-door policy, and you might want to think twice about it, preferring to be more selective. For a less all-encompassing approach,we can set up our system so that our chosen user can run a specified command, such as **`tcpdump`**, using **`sudo`**, and they won't have to pop in a password to do so:

```
USER    ALL=(ALL) NOPASSWD: /usr/sbin/tcpdump
```



## Leveraging Aliases

The **`/etc/sudoers`** file can be sorted out a bit better by sectioning things off with different types of "aliases". For example, we could set up three separate groups of users that might have a few members in common:

```
. . .
User_Alias      GROUPONE = abby, brent, carl
User_Alias      GROUPTWO = brent, doris, eric, 
User_Alias      GROUPTHREE = doris, felicia, grant
. . .
```

{% hint style="info" %}
&#x20;**Group names must start with a capital letter**
{% endhint %}



With our alises set, we can then set about configuring **`sudo`** permissions. For example, we will allow members of **`GROUPTWO`** to update the apt database by creating a rule like this:

```
. . .
GROUPTWO    ALL = /usr/bin/apt-get update
. . .
```

If we do not specify a user/group to run as, as above, **`sudo`** defaults to the **root** user.

{% hint style="info" %}
Don't worry if you dont know what `apt` is yet - we cover that later on. I'm showing it here simply to show a command that requires administrative privileges.
{% endhint %}



Next, we can allow members of **`GROUPTHREE`** to shutdown and reboot the machine by creating a **command alias** and using that in a rule for **`GROUPTHREE`**:

```
. . .
Cmnd_Alias      POWER = /sbin/shutdown, /sbin/halt, /sbin/reboot, /sbin/restart
GROUPTHREE      ALL = power
. . .
```

Here, we have created a command alias called **`POWER`** that contains commands to power off and reboot the machine. We then allow the members of **GROUPTHREE** to execute these commands.



We can also create “**Run as**” aliases, which can replace the portion of the rule that specifies the user to execute the command as:

```
. . .
Runas_Alias     WEB = www-data, apache
GROUPONE        ALL = (Web) All
. . .
```

This will allow anyone who is a member of GROUPONE to execute commands as the www-data user or the apache user.

{% hint style="info" %}
Be aware that later rules will override earlier rules when there is a conflict between the two - be weary of conflicts.
{% endhint %}



## Lock Down Rules

You've got several options for getting more of a handle on how **`sudo`** responds when it's summoned. The **`updatedb`** command from the **`mlocate`** package is pretty tame on a system with just one user. If you fancy letting users run it with root powers without the faff of entering a password, you could lay down a rule like this:

```
. . .
GROUPONE      ALL = NOPASSWD: /usr/bin/updatedb
. . .
```

As we saw earlier, `NOPASSWD` is a “tag” that means no password will be requested. It has a companion command called **`PASSWD`**, which is the default behaviour. A tag is relevant for the rest of the rule unless overruled by its “twin” tag later down the line.

For instance, we can have a line like this:

```
. . .
GROUPTWO      ALL = NOPASSWD: /usr/bin/updatedb, PASSWD: /bin/kill
. . .
```

This would mean that any member of **`GROUPTWO`** can execute **`updatedb`** without being prompted for a password, however the use of **`kill`** would still prompt a password request.



Another helpful tag is **`NOEXEC`**, which can be used to prevent some dangerous behaviour in certain programs. For example, some programs, like **`less`**, can spawn other commands by typing this from within their interface:

```
!command_to_run
```

This basically executes any command the user gives it with the same permissions that **`less`** is running under, which can be quite dangerous. To restrict this, we could use a line like this:

```
. . .
username      ALL = NOEXEC: /usr/bin/less
```
