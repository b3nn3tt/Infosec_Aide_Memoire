# Other Administrative Accounts

You don’t hear much about logging in with other administrative user accounts (besides `root`) on Linux systems. It was a fairly common practice in UNIX systems to have several different administrative logins that allowed administrative tasks to be split among several users. For example, people sitting near a printer could have `lp` permissions to move print jobs to another printer if they knew a printer wasn’t working.

In any case, administrative logins are available with Linux; however, **logging in directly as those users is disabled by default**. The accounts are maintained primarily to provide ownership for files and processes associated with particular services.

When daemon processes are run under separate administrative logins, having one of those processes cracked does not give the cracker root permission and the ability to access other processes and files.\
Consider the following examples:

*   **lp**\
    User owns such things as the `/var/log/cups` printing log file and various printing cache and spool files. The home directory for `lp` is `/var/spool/lpd`

    \

* **apache**\
  User can set up content files and directories on an Apache web server. It is primarily used to run the web server processes (`httpd`) in RHEL and Fedora systems, while the `www-data` user runs the Apache service (`apache2`) on Ubuntu systems\

* **avahi**\
  User runs the `avahi` daemon process to provide zeroconf services on your network\

* **chrony**\
  User runs the `chronyd` daemon, which is used to maintain accurate computer clocks\

* **postfix**\
  User owns various mail server spool directories and files. The user runs the daemon processes used to provide the `postfix` service (master)\

* **bin**\
  User owns many commands in /bin in traditional UNIX systems. This is not the case in some Linux systems (such as Ubuntu, Fedora, and Gentoo) because `root` owns most executable files. The home directory of `bin` is `/bin`\

* **news**\
  User could do administration of Internet news services, depending on how you set permission for  `var/spool/news` and other news-related resources. The home directory for news is `/etc/news`\

* **rpc**\
  User runs the remote procedure calls daemon (`rpcbind`), which is used to receive calls for services on the host system. The `NFS` service uses the RPC service

By default, the administrative logins in the preceding list are disabled. You would need to change the default shell from its current setting (usually `/sbin/nologin` or `/bin/false`) to a real shell (typically `/bin/bash`) to be able to log in as these users. As mentioned earlier, however, they are really not intended for interactive logins.
