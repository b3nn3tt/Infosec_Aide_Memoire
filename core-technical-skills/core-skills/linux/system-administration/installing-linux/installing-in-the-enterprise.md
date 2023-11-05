# Installing in the Enterprise

If you're in charge of an armada of Linux machines in a hefty enterprise, manually trotting over to each one for setup would be nothing short of a nightmare. Thankfully, the savvy world of Linux has got you covered with automation magic. You can now set up a system where simply powering up a machine and booting from its network interface card can kickstart your bespoke Linux setup.

While we've been chatting a lot about installing Linux from DVDs or USB sticks, there's a whole universe of other options to get Linux up and running. Below, we'll take a stroll through the installation journey, pointing out alternatives and twists you can apply to tailor the process:



1. **Launch the installation medium**\
   To kick things off with a Linux install, you've got a smorgasbord of bootable options: CD, DVD, USB thumb drive, hard drive, or even a network card with [PXE](https://en.wikipedia.org/wiki/Preboot\_Execution\_Environment) (Preboot eXecution Environment) up its sleeve. Your computer will inspecty its boot sequence, check out the master boot record on the chosen medium, or scout the network for a PXE server to get things moving\

2. **Start the anaconda kernel**\
   The boot loader is your backstage pass to kickstart the whole Linux setup show. It's got one job: to spotlight the kernel and maybe an initial RAM disk that brings up the headliner, the Linux installer ([Anaconda](https://docs.anaconda.com/anaconda/install/linux/) for the RHEL crowd). All those media options we talked about before? They just need to give a nod to where the kernel and initial RAM disk are hanging out to get the ball rolling. If your package lineup isn't on the same medium, no dramas - the installer will ask where to fetch those packages from\

3. **Add kickstart or other boot options**\
   Boot options are like secret codes that fine-tune how the Linux installer struts its stuff. Among the neat tricks Fedora and RHEL can pull off is accepting a path to a [kickstart](https://en.wikipedia.org/wiki/Kickstart\_\(Linux\)) file passed right into the installer's kernel. Think of a kickstart file as a cheat sheet loaded with all the nitty-gritty details for the setup: root password, partitioning layout, what time zone you're in, thelist goes on... Once Anaconda boots up, it'll either shoot questions at you for the missing pieces or simply take all it needs from the kickstart file and run with it, automating the whole installation process\

4.  **Find software packages**\
    When you're getting a Linux system up and running, the installer doesn't need to have all the software packages on the same medium. It's enough to have a boot medium with just the kernel and an initial RAM disk - that's your ticket to getting the installer rolling.\


    Now, for the main event - grabbing the software packages - long story short, you've got options. If you've planned ahead and prepped a kickstart file, that file can point the installer to where all the RPM goodies are stashed. Or, if you're going manual, you can type in the repository's address during the installation.\


    And oh, the places you can pull these packages from! If you're old school, there's the trusty local CD or DVD. If you're connected to the network, an HTTP or FTP site can serve up your software. More of a network whiz? An NFS share or NFS ISO's have got you covered. And if it's all about that local touch, you can dip into a hard drive right in your machine. Whichever route you take, Linux is flexible enough to get what you need from where you want it.\

5. **Modify installation with kickstart scripts**\
   Scripts included in a kickstart can run commands you choose before or after the installation to further configure the Linux system. Those commands can add users, change permissions, create files and directories, grab files over the network, or otherwise configure the installed system exactly as you specify.



Although installing Linux in enterprise environments is beyond the scope of this gitbook, I want you to understand the technologies that are available when you want to automate the Linux installation process. Here are some of those technologies available to use with RedHat Enterprise Linux, along with links to where you can find more information about them:

## Installation Server

If you set up an installation server, you don’t have to carry the software packages around to each machine where you install RHEL. Essentially, you copy all of the software packages from the RHEL installation medium to a Webserver, FTP server, or NFS server, and then point to the location of that server when you boot the installer. The RHEL 8 Installation Guide describes how to set up a local or network installation source [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_a\_standard\_rhel\_installation/index#prepareinstallation-source\_preparing-for-your-installation).



## PXE Server

If you have a computer with a Network Interface Card (NIC) that supports PXE booting (most do these days), you can set your computer’s BIOS to boot from that NIC. If you have set up a PXE server on that network, that server can present a menu to the computer containing entries to launch an installation process. The RHEL Installation Guide provides information on how to set up PXE servers for installation [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_a\_standard\_rhel\_installation/index#booting-theinstallation-using-pxe\_booting-the-installer).



## Kickstart Files

To automate an installation completely, you create what is called a kickstart file. By passing a kickstart file as a boot option to a Linux installer, you can provide answers to all of the installation questions that you would normally have to click through.&#x20;

When you install RHEL, a kickstart file containing answers to all installation questions for the installation you just did is contained in the `/root/anaconda-ks.cfg` file. You can present that file to your next installation to repeat the installation configuration, or use that file as a model for different installations.

See the Advanced RHEL Installation Guide for information on performing a kickstart installation [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_an\_advanced\_rhel\_installation/index/#performing\_an\_automated\_installation\_using\_kickstart), and creating your own kickstart files [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_an\_advanced\_rhel\_installation/index/#creating-kickstart-files\_installing-rhel-as-an-experienced-user).
