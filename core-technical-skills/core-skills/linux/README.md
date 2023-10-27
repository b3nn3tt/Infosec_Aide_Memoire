---
description: What is Linux?
---

# Linux

![](<../../../.gitbook/assets/image (204).png>)

Linux is a computer Operating System, or "OS".&#x20;

{% hint style="info" %}
An operating system consists of the software that manages your computer and lets you run applications on it.
{% endhint %}

Here's a quick rundown of what Linux, and its \*nix cousins, can do:

*   **Detecting and preparing hardware**

    When you switch on (or "boot") your computer,  Linux takes a look at the components your computer has, such as the CPU, hard drive, network cards, and so on. It then loads the software (drivers and modules) needed to access those particular hardware devices.
*   **Managing processes and Multitasking**

    A modern system has to juggle many things at once, deciding who gets the CPU's time. It also helps kick-start, end, or shuffle the status of various processes
*   **Managing memory**

    Got RAM? Linux decides which application gets how much of it. And if things get tight, it uses something called swap space (space on a hard disk that is a substitute for physical memory)
*   **Providing user interfaces**

    An OS must provide ways of accessing and interacting with the system. Early Linux systems were accessed from a Command-Line Interpreter (CLI) called the "shell". Today, modern Graphical User Interfaces (GUI) are available as well
*   **Controlling filesystems**

    Filesystem structures are built into the operating system (or loaded as **modules**). Linux controls "who" gets to see and do "what" with files and folders (known in Linux as directories)
*   **Providing user access and authentication**

    Linux is big on personal space. Different users get their own accounts, so they're the masters of their domains. Creating user accounts and allowing boundaries to be set between users is a core feature of the OS.
*   **Offering administrative utilities**

    Fancy doing a bit of system admin? Linux has got a tonne of commands and tools for you. Nowadays, nifty Web UI tools like [**Cockpit**](https://cockpit-project.org/) have lowered the bar for doing complex administrative tasks, which Im a big fan of
* **Starting up services**\
  To use printers, handle log messages, and provide a variety of system and network services, processes called **daemons** run in the background, waiting for requests to come in. Many types of services run in Linux. Linux offers a variety of ways to start and stop such services.&#x20;
* **Programming tools**\
  If you're into coding, Linux has a treasure trove of utilities to craft applications or add some special touches

As a Linux wrangler, you've got to get your head around all of these, and while the pretty graphical tools are nice, knowing your way around the shell command line is a must!

### But wait, there's more!

Modern Linux has evolved a lot from its UNIX ancestors. Check out these advanced features:

*   **Clustering**

    Fancy making multiple systems look like one big system? That's clustering. Services can move between cluster nodes without users noticing a thing
*   **Virtualisation**

    Linux can host virtual systems. So, on one machine, you might have several virtual Linux systems, Windows, BSD, and others. They all appear and behave like separate computers. The the brains behind this magic - KVM and XEN
*   **Cloud computing**

    If you're thinking **BIG**, then Linux-based cloud platforms like **OpenStack** and **Red Hat Virtualisation** (or its upstream project, **oVirt**) are the way to go. They manage virtual systems at scale, networks, users, and storage. Projects that manage containerised applications, such as **Kubernetes** are also an option
*   **Real-time computing**

    Linux can be configured for real-time computing, where high priority processes can expect fast, predictable attention
*   **Specialized storage**

    Beyond the humble hard disk, Linux plays nice with many local and network storage options. Think iSCSI, FibreChannel, or Infiniband. And if you're really ambitious, there's full-blown Open-Source platforms like [Ceph](https://ceph.io) and [GlusterFS](https://www.gluster.org)

So, there you have it! A casual stroll through Linux land.
