# Partitioning Hard Disks

The hard disk(s) on your computer provide the permanent (non-volatile) storage area for your data, applications programs, and the operating system itself. Partitioning is the act of dividing a disk into logical areas that can be worked with separately. In Windows, you typically have one partition that consumes the whole hard disk. However, with Linux there are several reasons you may want to have multiple partitions:

* **Multiple operating systems**\
  If you install Linux on a PC that already has a Windows operating system, you may want to keep both operating systems on the computer. For all practical purposes, each operating system must exist on a completely separate partition. When your computer boots, you can choose which system to run\

* **Multiple partitions within an operating system**\
  To protect their entire operating system from running out of disk space, people often assign separate partitions to different areas of the Linux filesystem. For example, if `/home` and `/var` were assigned to separate partitions, then a gluttonous user who fills up the `/home` partition wouldn’t prevent logging daemons from continuing to write to log files in the `/var/log` directory.\
  \
  Multiple partitions also make doing certain kinds of backups (such as an image backup) easier. For example, an image backup of `/home` would be much faster (and probably more useful) than an image backup of the root filesystem\

* **Different Filesystem Types**\
  Different kinds of filesystems have different structures. Filesystems of different types must be on their own partitions. Also, you might need different filesystems to have different mount options for special features (such as read-only or user quotas). In most Linux systems, you need at least one filesystem type for the root of the filesystem, and one for your swap area. Filesystems on CD-ROM use the iso9660 filesystem type

{% hint style="info" %}
When you create partitions for Linux, you usually assign the filesystem type as Linux native, using the `ext2`, `ext3`,`ext4`, or `xfs` type on most Linux systems. If the applications that you are running require particularly long filenames, large file sizes, or many inodes (each file consumes an inode), you may want to choose a different filesystem type
{% endhint %}

During installation, systems such as Fedora, RHEL and Ubuntu let you partition your hard disk using graphical partitioning tools.

### Understand Different Partition Types

Many Linux distributions give you the option of selecting different partition types when you partition your hard disk during installation. Partition types include the following:

* **Linux Partitions**\
  Use this option to create a partition for an `ext2`, `ext3`, or `ext4` filesystem type that is added directly to a partition on your hard disk (or other storage medium). The `xfs` filesystem type can also be used on a Linux partition. In fact, `xfs` is now the default filesystem type for RHEL 8 systems\

* **Logical Volume Manager (LVM) Partitions**\
  Create an `LVM` partition if you plan to create or add to an `LVM` volume group. LVMs give you more flexibility in growing, shrinking, and moving partitions later than regular partitions do\

* **RAID Partitions**\
  Create two or more RAID partitions to create a RAID array. These partitions should be on separate disks to create an effective RAID array. RAID arrays can help improve performance, reliability, or both as those features relate to reading, writing, and storing your data\

* **Swap Partitions**\
  Create a swap partition to extend the amount of virtual memory available on your system
