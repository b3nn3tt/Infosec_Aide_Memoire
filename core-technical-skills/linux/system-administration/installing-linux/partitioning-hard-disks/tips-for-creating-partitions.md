# Tips for Creating Partitions

Changing your disk partitions to handle multiple operating systems can be very tricky, in part because each operating system has its own ideas about how partitioning information should be handled as well as different tools for doing it. Here are some tips to help you get it right:

1. If you are creating a dual-boot system, particularly for a Windows system, try to install the Windows operating system first after partitioning your disk. Otherwise, the Windows installation may make the Linux partitions inaccessible 
2. The `fdisk` man page recommends that you use partitioning tools that come with an operating system to create partitions for that operating system. For example, the Windows `fdisk` knows how to create partitions that Windows will like, and the Linux `fdisk` will happily make your Linux partitions. After your hard disk is setup for dual boot, however, you should not go back to Windows-only partitioning tools. Use Linux `fdisk` or a product made for multi-boot systems, such as [Acronis Disk Director](https://www.acronis.com/en-gb/products/disk-director/?gclid=EAIaIQobChMIx8aAs-Ke8wIVhO_tCh1nRAwBEAAYASAAEgLZifD_BwE) 
3. A master boot record \(MBR\) partition table **can contain four primary partitions**, one of which can be marked to contain **184 logical drives**. On a GPT partition table, you can have a maximum of 128 primary partitions on most operating systems, including Linux. You typically won’t need nearly that many partitions. If you need more partitions, use `LVM` and create as many logical volumes as you like.

If you are using Linux as a desktop system, you probably don’t need lots of different partitions. However, some very good reasons exist for having multiple partitions for Linux systems that are shared by lots of users or are public web servers or file servers.

Having multiple partitions within Fedora or RHEL, for example, offers the following advantages:

* **Protection from Attacks** Denial-of-service attacks sometimes take actions that try to fill up your hard disk. If public areas, such as `/var`, are on separate partitions, a successful attack can fill up a partition without shutting down the whole computer. 

{% hint style="info" %}
Because `/var` is the default location for web and FTP servers, and is expected to hold lots of data, entire hard disks often are assigned to the `/var` filesystem alone
{% endhint %}

* **Protection from Corrupted Filesystems** If you have only one filesystem \(`/`\), its corruption can cause the whole Linux system to be damaged. Corruption of a smaller partition can be easier to fix, and often allows the computer to stay in service while the correction is made

The following table lists some directories that you may want to consider making into separate filesystem partitions:

| Directory | Explanation |
| :--- | :--- |
| `/boot` | Sometimes, the BIOS in older PCs can access only the first 1024 cylinders of your hard disk. To make sure that the information in your `/boot` directory is accessible to the BIOS, create a separate disk partition for `/boot`. Even with several kernels installed, there is rarely a reason for `/boot` to be larger than 1024 MiB \(mebibyte\). |
| `/usr` | This directory structure contains most of the applications and utilities available to Linux users. The original theory was that if `/usr` were on a separate partition, you could mount that filesystem as read-only after the operating system had been installed. This would prevent attackers from replacing or removing important system applications with their own versions that may cause security problems.   A separate `/usr` partition is also useful if you have diskless workstations on your local network. Using NFS, you can share `/usr` over the network with those workstations |
| `/var` | Your FTP \(`/var/ftp`\) and web server \(`/var/www`\) directories are, by default in many Linux systems, stored under `/var`. Having a separate `/var` partition can prevent an attack on those facilities from corrupting or filling up your entire hard disk |
| `/home` | Because your user account directories are located in this directory, having a separate `/home` partition can prevent a reckless user from filling up the entire hard disk. It also conveniently separates user data from your operating system for easy backups or new installs.  Often, `/home` is created as an `LVM` logical volume, so it can grow in size as user demands increase. It may also be assigned user quotas to limit disk use |
| `/tmp` | Protecting `/tmp` from the rest of the hard disk by placing it on a separate partition can ensure that applications that need to write to temporary files in `/tmp` can complete their processing, even if the rest of the disk fills up |

Although people who use Linux systems rarely see a need for lots of partitions, those who maintain and occasionally have to recover large systems are thankful when the system they need to fix has several partitions. Multiple partitions can limit the effects of deliberate damage \(such as denial-of-service attacks\), problems from errant users, and accidental filesystem corruption.

