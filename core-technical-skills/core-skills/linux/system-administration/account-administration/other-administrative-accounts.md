# Other Administrative Accounts

You don't really hear much about logging in as different admin users (apart from **root**) on Linux systems. Back in the day with UNIX systems, it wasn't unusual to have a few admin logins knocking around so you could divvy up the admin work between a few users. Often that would be someone perched next to a printer could have **lp** permissions to shuffle print jobs to a different printer if they saw that one was out of order.

Still, admin logins are a thing with Linux; it's just that **you can't normally log in directly as these users**. They're mainly there to claim ownership over files and processes that are tied to specific services.

Running daemon processes under their own admin logins means that if one process gets compromised, the attacker doesn't automatically get **root** access to meddle with other processes and files.

Have a look at these examples:

* **lp**\
  User owns such things as the **`/var/log/cups`** printing log file and various printing cache and spool files. The home directory for **`lp`** is **`/var/spool/lpd`**\

* **apache**\
  Users can set up content files and directories on an Apache web server. It is primarily used to run the web server processes (**`httpd`**) in RHEL and Fedora systems, while the **`www-data`** user runs the Apache service (**`apache2`**) on Ubuntu systems\

* **avahi**\
  User runs the **`avahi`** daemon process to provide zeroconf services on your network\

* **chrony**\
  User runs the **`chronyd`** daemon, which is used to maintain accurate computer clocks\

* **postfix**\
  User owns various mail server spool directories and files. The user runs the daemon processes used to provide the **`postfix`** service (master)\

* **bin**\
  User owns many commands in **`/bin`** in traditional UNIX systems. This is not the case in some Linux systems (such as Ubuntu, Fedora, and Gentoo) because **`root`** owns most executable files. The home directory of **bin** is **`/bin`**\

* **news**\
  User could do administration of Internet news services, depending on how you set permission for **`var/spool/news`** and other news-related resources. The home directory for news is **`/etc/news`**\

* **rpc**\
  User runs the remote procedure calls daemon (**`rpcbind`**), which is used to receive calls for services on the host system. The `NFS` service uses the RPC service

By default, the administrative logins in the preceding list are disabled. You would need to change the default shell from its current setting (usually **`/sbin/nologin`** or **`/bin/false`**) to a real shell to be able to log in as these users. As mentioned earlier, however, they are really not intended for interactive logins.
