---
description: It's time to learn to administer all the things.
---

# System Administration

## Navigating the Basics

If you are planning on using Linux to get things done, then there are some core topics we need to look at:

* **Installing Linux**\
  Here's where we'll begin, setting up your Linux system with precision. It's about laying the foundation for your secure computing environment.
* **Using the root login, and User Administration**\
  We'll examine the powerful root login, and how to manage users effectively
* **Understanding administrative commands, config files, and log files**\
  This is where the finesse comes in. We'll explore essential administrative commands, tweak configuration files, and interpret log files to ensure everything's ticking along nicely
* **Graphical administration**\
  For those who prefer a visual approach, we'll dive into managing your system with graphical tools. It's the difference between conducting the orchestra with a baton rather than a score
* **Working with devices and filesystems**\
  Finally, we'll get to grips with the devices and filesystems that underpin your system. It's about understanding the storage space where all the magic happens



## Understanding Linux: The Multiuser Marvel!

Linux, following in the grand UNIX tradition, is built for sharing. Imagine it like a bustling train station, designed to let multiple folks travel simultaneously, each with their own ticket and destination. Multiuser capabilities mean that several people can have their own area on a single Linux system, with all their bits and bobs kept safe from prying eyes.

Now, multitasking is another feather in its cap, letting numerous users run a whole range of programs at once, with everyone free to juggle multiple apps without a hitch.

And when it comes to networking, Linux is quite the social butterfly. Thanks to its slick networking protocols and applications, it reaches out and connects with users and computers across the globe, stretching its capabilities far and wide.

At the helm of this digital ecosystem is the **System Administrator**, or _SysAdmin_ as it is often referred to. This is the maestro conducting the symphony of Linux's resources, making sure every note hits just right.

Even if you're the sole navigator of your Linux system, think of system administration as a VIP section you'll need special access to. The most confidential tasks require the 'root user' credentials – think of it as having the master key to the system's castle. Or, for a temporary pass, you'd typically wave the 'sudo' command like a magic wand to temporarily grant you superuser powers.

For everyday users without the root password, the system's secrets remain just that – secret. It's like the system's got an unbreakable spell on its most sacred tomes, especially the security spells that guard passwords and such.

Given that Linux system administration is a bit like exploring a vast, uncharted territory, we're going to focus on the compass and map basics. We'll look at the essential toolkit you'll need for personal desktop journeys or small server expeditions. And beyond the starting kit, we'll also guide you through managing filesystems and keeping an eagle eye on how your Linux system is performing.



## **The Art of System Administration**

Think of the system administrator's role as the captain of the ship: essential for navigating the high seas, separate from the passengers enjoying the cruise. On a bustling system with a crew of users, having a dedicated captain - or admin - is not just about order; it's a matter of security. This role separation also means that users can't accidentally toss the system overboard while they're simply workgin on a document, or browsing the internet.

As the captain (or Sysadmin) of a Linux system, you usually step aboard as a regular crew member (standard user). You'll only don the captain's hat - that is, leverage administrative privileges - when there's a need to steer the ship. This magic act is commonly performed using one of the following:

*   **`su:`** Substitute user, or **`su`,** is used to open a shell as another user on the system. Typically, su is used to "switch" to the root user. After the shell is open, the administrator can run multiple commands and then **exit** to return to a shell as a regular user

    **`sudo:`** This is more like a temporary badge of power. With **`sudo`**, you perform just one action with administrative privileges, then it's back to regular duties. It's very quick and efficient. On distributions like Ubuntu and Fedora, the initial user account created gets this privilege by default. RHEL, on the other hand, makes you pick if you want to hand this privilege to your user account during setup
* **`Cockpit - Browser-based Administration:`** RHEL, Fedora, and several other Linux distributions, have committed to [Cockpit](https://cockpit-project.org/) as their primary **browser-based** system administration facility. With Cockpit enabled, you can monitor and change your system’s general activities, storage, networking, accounts, services, and other features
* **`Graphical windows:`** Before Cockpit was widely available, RHEL, Fedora, and other Linux distributions offered individual graphical administration tools that were launched by commands beginning with **`system-config-*`**. Although most of these administration tools are not being offered in the latest release of RHEL and Fedora, they are noted here because they are still available in older Linux releases

Certain tasks need the keys to the kingdom, so to speak, and are reserved for the **root** user because they could shake up the whole system or mess with its security or stability. Here's a rundown of the typical areas where a system admin, wearing the root user hat, needs to step in:

* **`Filesystems:`** Right after installation, Linux is all set for use. But say someone wants to plug in extra storage or rejig the existing file system setup, they'll need the admin's say-so. Plus, the root user can access or modify anyone's files - handy for creating backups to safeguard data
* **`Software installation:`**  To fend off rogue software, installing anything that all users can access is a root-level job. Regular users aren't totally out of luck; they can still add some software in their own space and list installed system-wide software
* **`User accounts:`** Adding or removing user or group accounts is a **root-only** capability
* **`Network interfaces:`** Back in the day, tweaking network settings was a job for the root user. These days, with tools like Network Manager, even regular users on their Linux desktop can manage network interfaces, especially wireless ones as they roam about
* **`Servers:`** Whether it's setting up or managing web, file, mail servers, or the whole shebang, you need root access. Starting and stopping these services too. However, regular users can contribute content, like web pages, if things are set up to allow it. And for added security, services run under their own special user accounts, such as **`apache`** (for the httpd service) and **`rpc`** (for the rpcbind service), so even if one service gets compromised, the others and the system remain secure
* **`Security features:`** Crafting firewalls, setting up access controls - that's root territory. This includes keeping an eye on service usage to prevent and respond to any overuse or misuse, ensuring the system's services run smoothly and securely
