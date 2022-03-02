# Managing Running Processes

&#x20;In this section we will look at:

* Displaying processes\

* Running processes in the foreground and background\

* Killing and renicing processes

In addition to being a multiuser operating system, Linux is a multitasking system. Multitasking means that many programs can be running at the same time.

{% hint style="info" %}
An instance of a running program is referred to as a process.
{% endhint %}

Linux provides tools for listing running processes, monitoring system usage, and stopping (or killing) processes when necessary. From a shell, you can launch processes and then pause, stop, or kill them. You can also put them in the background and bring them to the foreground.

This section describes tools such as `ps`, `top`, `kill`, `jobs`, and other commands for listing and managing processes.



## Understanding Processes

A process is a running instance of a command. For example, there may be one `vi` command on the system. But if `vi` is currently being run by 15 different users, that command is represented by 15 different running processes.

A process is identified on the system by what is referred to as a process ID (**PID**). That PID is unique for the current system. In other words, no other process can use that number as its process ID while that first process is still running. However, after a process has ended, another process can reuse that number.

Along with a process ID number, other attributes are associated with a process. Each process, when it is run, is associated with a particular user account and group account. That account information helps determine what system resources the process can access. For example, a process run as the `root` user has much more access to system files and resources than a process running as a regular user.

The ability to manage processes on your system is critical for a Linux system administrator. Sometimes, runaway processes may be killing your system’s performance. Finding and dealing with processes, based on attributes such as memory and CPU usage, are covered in this section.







