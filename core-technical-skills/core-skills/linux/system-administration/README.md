---
description: It's time to learn to administer all the things.
---

# System Administration

In this section, we will explore:

* Installing Linux
* Using the root login, and User Administration
* Understanding administrative commands, config files, and log files
* Graphical administration
* Working with devices and filesystems

Linux, like other UNIX-based systems, was intended for use by more than one person at a time. **Multiuser** features enable many people to have accounts on a single Linux system with their data kept secure from others. **Multitasking** enables many people to run many programs on the computer at the same time, with each person able to run more than one program.&#x20;

Sophisticated networking protocols and applications make it possible for a Linux system to extend its capabilities to network users and computers around the world. The person assigned to manage all of a Linux system’s resources is called the **System Administrator**, or _SysAdmin_ for short.

Even if you are the only person using a Linux system, system administration is still set up to be separate from other computer use. To do most administrative tasks, you need to be logged in as the **root** user, otherwise known as the _superuser_, or to get root permission temporarily, usually using the `sudo` command. Regular users who don’t have root permission cannot change, or in some cases even see, some of the configuration information for a Linux system. In particular, security features such as stored passwords are protected from general view.

Because Linux system administration is such a huge topic, this section focuses on the general principles of Linux system administration. In particular, it examines some of the basic tools that you need to administer a Linux system for a personal desktop or on a small server. Beyond the basics, this section also teaches you how to work with filesystems and monitor the setup and performance of your Linux system.

## **Understanding System Administration**

Separating the role of system administrator from that of other users has several effects. For a system that has many people using it, limiting who can manage it enables you to keep it more secure. A separate administrative role also prevents others from casually harming your system when they are just using it to write a document or browse the Internet.

If you are the system administrator of a Linux system, you generally log in as a regular user account and then leverage administrative privileges when you need them. This is often done with one of the following:

*   **`su:`** Often, su is used to open a shell as root user. After the shell is open, the administrator can run multiple commands and then exit to return to a shell as a regular user

    **`sudo:`** With `sudo`, a regular user is given root privileges, but only when that user runs the `sudo` command to run another command. After running that one command with `sudo`, the user is immediately returned to a shell and acts as the regular user again. By default, [Ubuntu](https://ubuntu.com/) and [Fedora](https://getfedora.org/) assign `sudo` privilege to the first user account when those systems are installed. This is not done by default in RHEL, although during RHEL installation, you can choose for your first user to have `sudo` privilege if you’d like
* **`Cockpit - Browser-based Administration:`** RHEL, Fedora, and several other Linux distributions, have committed to [Cockpit](https://cockpit-project.org/) as their primary browser-based system administration facility. With Cockpit enabled, you can monitor and change your system’s general activities, storage, networking, accounts, services, and other features
* **`Graphical windows:`** Before Cockpit was widely available, RHEL, Fedora, and other Linux distributions offered individual graphical administration tools that were launched by commands beginning with `system-config-*`. Although most of these administration tools are not being offered in the latest release of RHEL and Fedora, they are noted here because they are still available in older Linux releases

Tasks that can be done only by the root user tend to be those that affect the system as a whole or impact the security or health of the system. Following is a list of common features that a system administrator is expected to manage:

* **`Filesystems:`** When you first install Linux, the directory structure is set up to make the system usable. However, if users later want to add extra storage or change the filesystem layout outside of their home directory, they need administrative privileges to do that. Also, the root user has permission to access files owned by any user. As a result, the root user can copy, move, or change any other user’s files—a privilege needed to make backup copies of the filesystem for safekeeping.
* **`Software installation:`**  Because malicious software can harm your system or make it insecure, you need root privilege to install software so that it is available to all users on your system. Regular users can still install some software in their own directories and can list information about installed system software
* **`User accounts:`** Only the root user can add and remove user accounts and group accounts
* **`Network interfaces:`** In the past, the root user had to configure network interfaces and start and stop those interfaces. Now, many Linux desktops allow regular users to start and stop network interfaces from their desktop using Network Manager. This is particularly true for wireless network interfaces, which can come and go by location as you move your Linux laptop or handheld device around
* **`Servers:`** Configuring web servers, file servers, domain name servers, mail servers, and dozens of other servers requires root privilege, as does starting and stopping those services. Content, such as web pages, can be added to servers by non-root users if you configure your system to allow that. Services are often run as special administrative user accounts, such as `apache` (for the httpd service) and `rpc` (for the rpcbind service). So, if someone cracks a service, they can’t get root privilege to other services or system resources
* **`Security features:`** Setting up security features, such as firewalls and user access lists, is usually done with root privilege. It’s also up to the root user to monitor how the services are being used and to make sure that server resources are not exhausted or abused
