# ps

## Listing Processes with ps

The most common utility for checking running processes is the `ps` command. Use it to see which programs are running, the resources they are using, and who is running them. The following is an example of the ps command:

```
ps u
```

![](<../../../../../../.gitbook/assets/image (79).png>)

In this example, the u option (equivalent to -u) asks that usernames be shown, as well as other information such as:

* The time the process started
* Memory
* CPU usage for processes associated with the current user

The processes shown are associated with the current terminal, `tty1`. The concept of a terminal comes from the old days when people worked exclusively from character terminals, so a terminal typically represented a single person at a single screen. Nowadays, you can have many “terminals” on one screen by opening multiple virtual terminals or Terminal windows on the desktop.

In this shell session, not much is happening. The first process shows that the user named b3nn3tt opened a bash shell after logging in. The next process shows that b3nn3tt has run the `ps u` command.

Let's break down the output further:

| Column Name | Description                                                                                                                                                                                       |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `USER`      | Shows the name of the user who started the process                                                                                                                                                |
| `PID`       | Each process is represented by a unique ID number referred to as a process ID, or PID. You can use the PID if you ever need to kill a runaway process or send another kind of signal to a process |
| `%CPU`      | %CPU show the percentages of the processor that the process is consuming                                                                                                                          |
| `%MEM`      | %MEM show the percentages of the system RAM that the process is consuming                                                                                                                         |
| `VSZ`       | The Virtual Set Size, which shows the size of the image process (in kilobytes)                                                                                                                    |
| `RSS`       | The Resident Set Size, which shows the size of the program in memory                                                                                                                              |
| `TTY`       | The terminal device being used for the login session                                                                                                                                              |
| `STAT`      | Represents the state of the process, with R indicating a currently running process and S representing a sleeping process                                                                          |
| `START`     | Shows the time the process began running                                                                                                                                                          |
| `TIME`      | Shows the cumulative system time used. Many commands consume very little CPU time, as reflected by 0:00 for processes that haven’t even used a whole second of CPU time                           |
| `COMMAND`   | The command that was executed, or the name of the running service                                                                                                                                 |

{% hint style="info" %}
Several other values can appear under the STAT column. For example, a plus sign (`+`) indicates that the process is associated with the foreground operations.

The VSZ and RSS sizes may be different because VSZ is the amount of memory allocated for the process, whereas RSS is the amount that is actually being used. RSS memory represents physical memory that cannot be swapped
{% endhint %}

Many processes running on a computer are not associated with a terminal. A normal Linux system has many processes running in the background. Background system processes perform such tasks as logging system activity or listening for data coming in from the network. They are often started when Linux boots up and run continuously until the system shuts down.

Likewise, logging into a Linux desktop causes many background processes to kick off, such as processes for managing audio, desktop panels, authentication, and other desktop features. To page through **all of the processes running on your Linux system for the current user**, enter the following command:

```
ps ux
```

![A list of ALL processes running for the current user](<../../../../../../.gitbook/assets/image (178).png>)

&#x20;To page through **all processes running for ALL users on your system**, use the `ps aux` command as follows:

```
ps aux
```

![A list of ALL processes running for ALL users](<../../../../../../.gitbook/assets/image (129).png>)

The ps command can be customized to display selected columns of information, and to sort information by one of those columns. Using the `-o` option, you can use keywords to indicate the columns you want to list with ps. For instance, the next example lists every running process (`-e`) and then follows the `-o` option with every column of information I want to display:

```
ps -eo pid,user,uid,group,gid,vsz,rss,comm
```

![Specified desired output, sorted by PID](<../../../../../../.gitbook/assets/image (62).png>)

{% hint style="info" %}
By default, output is sorted by process ID number
{% endhint %}

If you want to sort by a specific column, you can use the `sort=` option. For example, to see which processes are using the most memory, I sort by the vsz field:

```
ps -eo pid,user,group,gid,vsz,rss,comm --sort=vsz
```

![Specified desired output, sorted by VSZ to determine most memory hungry process (Lower first)](<../../../../../../.gitbook/assets/image (190).png>)

The previous command sorts from **lowest memory use to highest**. If I wanted to see the highest consumers first, I could put a hyphen in front of that option to sort:

```
ps -eo pid,user,group,gid,vsz,rss,comm --sort=-vsz
```

![Specified desired output, sorted by VSZ to determine most memory hungry process (Highest first)](<../../../../../../.gitbook/assets/image (3) (1).png>)
