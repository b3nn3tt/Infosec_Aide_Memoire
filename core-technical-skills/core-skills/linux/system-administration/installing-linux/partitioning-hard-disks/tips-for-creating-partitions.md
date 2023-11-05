# Tips for Creating Partitions

Changing your disk partitions to handle multiple operating systems can be very tricky, in part because each operating system has its own ideas about how partitioning information should be handled, as well as different tools for doing it. Here are some tips to help you get it right:

1. **Operating System Installation Order**\
   When setting up a dual-boot environment with Windows and Linux, it's generally best to install Windows first. Windows' installation can overwrite the boot loader that recognizes Linux, making it challenging to boot into the Linux OS if it's installed first\

2. **Partitioning Tools**\
   Use the partitioning tools native to each operating system to create its respective partitions. Windows has its own partitioning tools that understand its filesystems, and similarly, Linux distributions come with tools like **`fdisk`** or **`gparted`**. After the initial setup, avoid using Windows partitioning tools on a dual-boot system, as they may not be aware of Linux partitions and could cause data loss. Instead, use Linux **`fdisk`**, or a product made for multi-boot systems, such as [Acronis Disk Director](https://www.acronis.com/en-gb/products/disk-director/?gclid=EAIaIQobChMIx8aAs-Ke8wIVhO\_tCh1nRAwBEAAYASAAEgLZifD\_BwE)\

3. **Master Boot Record (MBR) vs. GUID Partition Table (GPT)**\
   MBR is limited to **four** primary partitions (one of which can be marked to contain **184 logical drives**), but GPT allows for many more (up to 128 on most systems). For systems requiring numerous partitions, the use of GPT is recommended. Alternatively, on MBR disks, one can use **`LVM`** and create an extended partition to house multiple logical drives



For desktop users, a simple partitioning scheme is often sufficient. However, for servers or systems with multiple users, there are advantages to having separate partitions for areas like **`/home`**, **`/var`**, and **`/tmp`**. This approach can enhance security, simplify backup processes, and avoid system issues due to individual partitions filling up:

* **Protection from Attacks**\
  Denial-of-service attacks sometimes take actions that try to fill up your hard disk. If public areas, such as **`/var`**, are on separate partitions, a successful attack can fill up a partition without shutting down the whole computer.&#x20;

{% hint style="info" %}
Because **`/var`** is the default location for web and FTP servers, and is expected to hold lots of data, entire hard disks often are assigned to the **`/var`** filesystem alone
{% endhint %}

* **Protection from Corrupted Filesystems**\
  If you have only one filesystem (**`/`**), its corruption can cause the whole system to collapse. Corruption of a smaller partition is much easier to fix, and often allows the computer to stay in service while the correction is made.

The following table lists some directories that you may want to consider making into separate filesystem partitions:

| Directory | Explanation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `/boot`   | Sometimes, the BIOS in older PCs can access only the first 1024 cylinders of your hard disk. To make sure that the information in your `/boot` directory is accessible to the BIOS, create a separate disk partition for `/boot`. Even with several kernels installed, there is rarely a reason for `/boot` to be larger than 1024 MiB (mebibyte).                                                                                                                                                                                                                                                                                               |
| `/usr`    | <p>This directory structure contains most of the applications and utilities available to Linux users. The original theory was that if <code>/usr</code> were on a separate partition, you could mount that filesystem as read-only after the operating system had been installed. This would prevent attackers from replacing or removing important system applications with their own versions that may cause security problems. <br><br>A separate <code>/usr</code> partition is also useful if you have diskless workstations on your local network. Using NFS, you can share <code>/usr</code> over the network with those workstations</p> |
| `/var`    | Your FTP (`/var/ftp`) and web server (`/var/www`) directories are, by default in many Linux systems, stored under `/var`. Having a separate `/var` partition can prevent an attack on those facilities from corrupting or filling up your entire hard disk                                                                                                                                                                                                                                                                                                                                                                                       |
| `/home`   | <p>Because your user account directories are located in this directory, having a separate <code>/home</code> partition can prevent a reckless user from filling up the entire hard disk. It also conveniently separates user data from your operating system for easy backups or new installs.<br><br>Often, <code>/home</code> is created as an <code>LVM</code> logical volume, so it can grow in size as user demands increase. It may also be assigned user quotas to limit disk use</p>                                                                                                                                                     |
| `/tmp`    | Protecting `/tmp` from the rest of the hard disk by placing it on a separate partition can ensure that applications that need to write to temporary files in `/tmp` can complete their processing, even if the rest of the disk fills up                                                                                                                                                                                                                                                                                                                                                                                                         |



## Summary

If you're dealing with a big Linux system that a lot of people use, or if it's a server that's out there on the web, having several partitions can be a real lifesaver. It helps to keep the damage to a minimum if things go sideways, whether it's because someone's up to no good, you've got users who are a bit clumsy, or just a spot of bad luck with the system getting corrupted. It's like putting up good fences in a massive garden; it keeps the chaos contained if something starts to go pear-shaped in one corner.
