# Create Aliases

The `/etc/sudoers` file can be organised more easily by grouping things with various kinds of “aliases”. For instance, we can create three different groups of users, with overlapping membership:

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









