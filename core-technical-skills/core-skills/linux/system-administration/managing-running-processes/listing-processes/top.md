# top

The `top` command provides a screen-oriented means of displaying processes running on your system. With `top`, the default is to display processes based on how much CPU time they are currently consuming. However, you can sort by other columns as well.

After you identify a misbehaving process, you can also use top to kill (completely end) or renice (reprioritize) that process.

{% hint style="info" %}
If you want to be able to kill or renice any processes, you need to run `top` as the `root` user. If you just want to display processes and possibly kill or change your own processes, you can do that as a regular user
{% endhint %}

```
top
```

![An example of running top](<../../../../../../.gitbook/assets/image (77).png>)

General information about your system appears at the top of the output, followed by information about each running process (or at least as many as will fit on your screen). At the top, you can see how long the system has been up, how many users are currently logged in to the system, and how much demand there has been on the system for the past 1, 5,and 10 minutes. Other general information includes how many processes (tasks) are currently running, how much CPU is being used, and how much RAM and swap are available and being used.

The following are also available:

* `h:` see help options, and then press any key to return to the top display
* `M:` to sort by memory usage instead of CPU, and then press **`P`** to return to sorting by CPU
* `1:` to toggle, showing CPU usage of all your CPUs if you have more than one CPU on your system
* `R:` to reverse sort your output
* `u:` and enter a username to display processes only for a particular user

&#x20;When you are done, press `q` to quit the program.



## **Renicing or Killing Processes**

A common practice is to use top to find processes that are consuming too much memory or processing power and then act on those processes in some way. A process consuming too much CPU can be reniced to give it less priority to the processors. A process consuming too much memory can be killed.

With top running, here’s how to renice or kill a process:

* **Renicing a Process**\
  Note the process ID (**PID**) of the process you want to renice and press `r`. When the PID to renice message appears, type the process ID of the process you want to renice. When prompted to Renice PID to value, type in a number from –20 to 19 - _**See “Setting processor priority with nice and renice” later in this section for information on the meanings of different renice values**_.\

* **Killing a Process**\
  Note the process ID of the process you want to kill and press `k`. Type 15 to terminate cleanly, or 9 to just kill the process outright - _**See “Killingprocesses with kill and killall” later in this chapter for more information on usingdifferent signals you can send to processes**_.
