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

The /etc/sudoers file can be sorted out a bit better by sectioning things off with different types of "aliases". For example, we could set up three separate groups of users that might have a few members in common:

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



We can then allow members of `GROUPTWO` to update the apt database by creating a rule like this:

```
. . .
GROUPTWO    ALL = /usr/bin/apt-get update
. . .
```

If we do not specify a user/group to run as, as above, `sudo` defaults to the root user.



Next, we can allow members of `GROUPTHREE` to shutdown and reboot the machine by creating a **command alias** and using that in a rule for `GROUPTHREE`:

```
. . .
Cmnd_Alias      POWER = /sbin/shutdown, /sbin/halt, /sbin/reboot, /sbin/restart
GROUPTHREE      ALL = power
. . .
```

Here, we have created a command alias called `POWER` that contains commands to power off and reboot the machine. We then allow the members of GROUPTHREE to execute these commands.



We can also create “**Run as**” aliases, which can replace the portion of the rule that specifies the user to execute the command as:

```
. . .
Runas_Alias     WEB = www-data, apache
GROUPONE        ALL = (Web) All
. . .
```

This will allow anyone who is a member of GROUPONE to execute commands as the www-data user or the apache user.

{% hint style="info" %}
Be aware that later rules will override earlier rules when there is a conflict between the two - be weary of conflicts
{% endhint %}



















