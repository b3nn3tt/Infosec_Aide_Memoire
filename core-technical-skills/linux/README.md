# Linux

![](../../.gitbook/assets/image%20%2820%29.png)

## What is Linux?

Linux is a computer operating system. An operating system consists of the software that manages your computer and lets you run applications on it. The features that make up Linux, and similar _**\*nix**_ computer operating systems, include the following:

* **Detecting and preparing hardware**

  When the Linux system boots up \(when you turn on your computer\), it looks at the components on your computer \(CPU, hard drive, network cards, and so on\), and loads the software \(drivers and modules\) needed to access those particular hardware devices.

* **Managing processes**

  The operating system must keep track of multiple processes running at the same time and decide which have access to the CPU and when. The system also must offer ways of starting, stopping, and changing the status of processes.

* **Managing memory**

  RAM and swap space \(extended memory\) must be allocated to applications as they need memory. The operating system decides how requests for memory are handled.

* **Providing user interfaces**

  An operating system must provide ways of accessing the system. The first Linux systems were accessed from a command-line interpreter called the shell. Today, graphical desktop interfaces are commonly available as well.

* **Controlling filesystems**

  Filesystem structures are built into the operating system \(or loaded as modules\). The operating system controls ownership and access to the files and directories \(folders\) that the filesystems contain.

* **Providing user access and authentication**

  Creating user accounts and allowing boundaries to be set between users is a basic feature of Linux. Separate user and group accounts enable users to control their own files and processes.

* **Offering administrative utilities**

  In Linux, hundreds \(perhaps thousands\) of commands and graphical windows are available to do such things as add users, manage disks, monitor the network, install software, and generally secure and manage your computer. Web UI tools, such as [_**Cockpit**_](https://cockpit-project.org/), have lowered the bar for doing complex administrative tasks.

* **Starting up services**

  To use printers, handle log messages, and provide a variety of system and network services, processes called _**daemon processes**_ run in the background, waiting for requests to come in. Many types of services run in Linux. Linux provides different ways of starting and stopping these services. In other words, while Linux includes web browsers to view web pages, it can also be the computer that serves up web pages to others. Popular server features include web, mail, database, printer, file, DNS, and DHCP servers.

* **Programming tools**

  A wide variety of programming utilities for creating applications and libraries for implementing specialty interfaces are available with Linux.

As someone managing Linux systems, you need to learn how to work with those features just described. While many features can be managed using graphical interfaces, an understanding of the shell command line is critical for someone administering Linux systems. Modern Linux systems now go way beyond what the first UNIX systems \(on which Linux was based\) could do. Advanced features in Linux, often used in large enterprises, include the following.

* **Clustering**

  Linux can be configured to work in clusters so that multiple systems can appear as one system to the outside world. Services can be configured to pass back and forth between cluster nodes while appearing to those using the services that they are running without interruption.

* **Virtualization**

  To manage computing resources more efficiently, Linux can run as a virtualisation host. On that host, you could run other Linux systems, Microsoft Windows, BSD, or other operating systems as virtual guests. To the outside world, each of those virtual guests appears as a separate computer. _**KVM**_ and _**Xen**_ are two technologies in Linux for creating virtual hosts.

* **Cloud computing**

  To manage large-scale virtualization environments, you can use full-blown cloud computing platforms based on Linux. Projects such as _**OpenStack**_ and _**Red Hat Virtualization**_ \(and its upstream oVirt project\) can simultaneously manage many virtualization hosts, virtual networks, user and system authentication, virtual guests, and networked storage. Projects such as _**Kubernetes**_ can manage containerized applications across massive datacentres.

* **Real-time computing**

  Linux can be configured for real-time computing, where high priority processes can expect fast, predictable attention.

* **Specialized storage**

  Instead of just storing data on the computer’s hard disk, you can store it on many specialized local and networked storage interfaces that are available in Linux. Shared storage devices available in Linux include iSCSI, FibreChannel, and Infiniband. Entire open source storage platforms include projects suchas [_Ceph_](https://ceph.io) and [_GlusterFS_](https://www.gluster.org).



