# kill and killall

Although usually used for ending a running process, the `kill` and `killall` commands can actually be used to send any valid signal to a running process.

Signals are represented by both numbers and names. Signals that you might send most commonly from a command include **`SIGKILL` (`9`)**, **`SIGTERM` (`15`)**, and **`SIGHUP` (`1`)**. The default signal is **`SIGTERM`**, which tries to terminate a process cleanly. Different processes respond to different signals. However, processes cannot block **`SIGKILL`** and **`SIGSTOP`** signals.

The following table shows the signals available in Linux:

| Signal    | Number       |
| --------- | ------------ |
| `SIGHUP`  | `1`          |
| `SIGINT`  | `2`          |
| `SIGQUIT` | `3`          |
| `SIGABRT` | `6`          |
| `SIGKILL` | `9`          |
| `SIGTERM` | `15`         |
| `SIGCONT` | `18, 19, 25` |
| `SIGSTOP` | `17, 19, 23` |



## **Using kill to Signal Process by PID**

Let's consider an example. Let's say you have run the top command, and you notice that the `bigcommand` process is consuming most of your processing power:

{% code title="TOP OUTPUT EXAMPLE" %}
```
PID   USER  PR NI VIRT RES  SHR S %CPU %MEM TIME+    COMMAND
10432 chris 20 0  471m 121m 18m S 99.9 3.2  77:01.76 bigcommand
```
{% endcode %}

So, we can see that the `bigcommand` process is consuming **99.9** percent of the CPU. You decide that you want to kill it so that other processes have a shot at the CPU. Here are some examples of the `kill` command that you can use, leveraging the process ID:

```
#Default sending of SIGTERM
kill 10432

#Manually selecting SIGTERM - achieves the same outcome as a default kill
kill -15 10432

#Manually selecting SIGKILL by name, not number
kill -SIGTERM 10432
```

{% hint style="info" %}
On occasion, a **`SIGTERM`** doesn’t kill a process, so you may need a **`SIGKILL`** to kill it. Instead of **`SIGKILL`**, you can use **`–9`** to get the same result
{% endhint %}

Another useful signal is **`SIGHUP`**. If, for example, something on your GNOME desktop, you could send the gnome-shell a **`SIGHUP`** signal to reread its configuration files and restart the desktop. If the process ID for gnome-shell were 1833, here are two ways you could send it a SIGHUP signal:

```
#Sending SIGHUP from numberic value
kill -1 1833

#Sending SIGHUP by shortened name
killall -HUP gnome-shell
```



## **Using killall to Signal a Process by Name**

With the `killall` command, you can signal processes by name instead of by process ID. The advantage is that you don’t have to look up the process ID of the process that you want to kill. The potential downside is that **you can kill more processes than you mean to if you are not careful**. For example, typing `killall bash` may kill a bunch of shells that you don’t mean to kill.

Like the `kill` command, `killall` uses **`SIGTERM`** (**`15`**) if you don’t explicitly enter a signal number. Also as with `kill`, you can send any signal you like to the process you name with `killall`. For example, if you see a process called `testme` running on your system and you want to kill it, you can simply enter the following:

```
killall -9 testme
```

{% hint style="info" %}
Whilst there is a natural danger, as outlined above, the `killall` command can be particularly useful if you want to kill a bunch of commands of the same name
{% endhint %}
