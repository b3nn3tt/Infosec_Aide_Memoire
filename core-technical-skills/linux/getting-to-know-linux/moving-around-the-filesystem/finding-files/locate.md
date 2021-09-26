# locate

On most Linux systems \(Fedora and RHEL included\), the **updatedb** command runs once per day to gather the names of files throughout your Linux system, adding them into a database. By running the `locate` command, you can query said database to find the location of files stored in it.

There are, like anything, advantages and disadvantages to this...

| Advantage | Disadvantage |
| :--- | :--- |
| The `locate` command finds files much faster than alternative methods because it searches a database instead of having to search the whole filesystem in live time | The `locate` command cannot find any files added to the system since the previous time the database was updated. |
|  | Not every file in your filesystem is stored in the database - _see below_ |

The contents of the`/etc/updatedb.conf` file limit which filenames are collected by pruning out select mount types, filesystem types, file types, and mount points. For example, filenames are not gathered from remotely mounted filesystems \(`CIFS`, `NFS`, and so on...\) or locally mounted CDs or DVDs \(iso9660\). Paths containing temporary files\(`/tmp`\) and spool files \(`/var/spool/cups`\) are also pruned. 

You can add items to prune \(or remove some items that you don’t want pruned\) from the locate database to suit your needs. For example, In RHEL 8, the `updatedb.conf` file contains the following:

```text
PRUNE_BIND_MOUNTS = "yes"
PRUNEFS = "9p afs anon_inodefs auto autofs bdev binfmt_misc cgroupcifs coda configfs cpuset debugfs devpts ecryptfs exofs fuse fuse.sshfs fusectl gfs gfs2 gpfs hugetlbfs inotifyfs iso9660 jffs2lustre mqueue ncpfs nfs nfs4 nfsd pipefs proc ramfs rootfs rpc_pipefs securityfs selinuxfs sfs sockfs sysfs tmpfs ubifs udf usbfsceph fuse.ceph"
PRUNENAMES = ".git .hg .svn .bzr .arch-ids {arch} CVS"
PRUNEPATHS = "/afs /media /mnt /net /sfs /tmp /udev /var/cache/ccache /var/lib/yum/yumdb /var/lib/dnf/yumdb /var/spool/cups /var/spool/squid /var/tmp /var/lib/ceph"
```

{% hint style="info" %}
As a regular user, you can't see any files from the locate database that you can't see in the filesystem normally. For example, if you can't type `ls` to view files in the `/root` directory, you can't `locate` files stored in that directory either.
{% endhint %}

## Using locate

When you search for a string, the string can appear anywhere in a file’s path. For example, if you search for `passwd`, you could turn up:

* `/etc/passwd`
* `/usr/bin/passwd`
* `/home/example/passwd/pwdfiles.txt`
* ...and any number of other places

If you add files to your system after `updatedb` runs, you can’t locate those files until `updatedb` runs again \(probably that night\). To get the database to contain all files up to the current moment, you can simply run `updatedb` from the shell as root \(or via `sudo`\).

Here are some examples of using the locate command to search for files:

```text
locate .bashrc
```

![Running locate to find any files that contain the string &quot;.bashrc&quot; in their name](../../../../../.gitbook/assets/image%20%2831%29.png)

{% hint style="info" %}
When run as a regular user, locate only finds `.bashrc` in `/etc/skel` and the user’s own home directory. However, when run as root, the same command locates `.bashrc` files in **everyone’s** home directory.
{% endhint %}

 Using locate `-i`, filenames are found **regardless of case sensitivity**.

