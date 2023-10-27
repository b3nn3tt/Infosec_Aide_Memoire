# Installing in the Enterprise

If you are managing dozens, hundreds, perhaps even thousands of Linux systems in a large enterprise, it would be a real pain to have to go to each computer to type and click through each installation. Fortunately, with modern Linux distributions, you can automate installation in such a way that all you need to do is to turn on a computer and boot from the computer’s network interface card to get your desired Linux installation.

Although up to this point we have focused on installing Linux from DVD or USB media, there are many other ways to launch a Linux installation, and many ways to complete an installation. The following descriptions step through the installation process and describe ways of changing that process along the way:

1. **Launch the installation medium**\
   You can launch an installation from any medium that you can boot from a computer: CD, DVD, USB drive, hard disk, or network interface card with [PXE](https://en.wikipedia.org/wiki/Preboot\_Execution\_Environment) support. The computer goes through its boot order and looks at the master boot record on the physical medium, or looks for a PXE server on the network\

2. **Start the anaconda kernel**\
   The job of the boot loader is to point to the special kernel (and possibly, an initial RAM disk) that starts the Linux installer called [Anaconda](https://docs.anaconda.com/anaconda/install/linux/). So, any of the media types just described simply needs to point to the location of the kernel and initial RAM disk to start the installation. If the software packages are not on the same medium, the installation process prompts you for where to get those packages\

3. **Add kickstart or other boot options**\
   Boot options (described later in this section) can be passed to the anaconda kernel to configure how it starts up. One option supported by Fedora and RHEL allows you to pass the location of a [kickstart](https://en.wikipedia.org/wiki/Kickstart\_\(Linux\)) file to the installer. That kickstart can contain all of the information needed to complete the installation; root password, partitioning, time zone, and so on, to configure the installed system further. After the installer starts, it either prompts for needed information or uses the answers provided in the kickstart file\

4. **Find software packages**\
   Software packages don’t have to be on the installation medium. This allows you to launch an installation from a boot medium that contains only a kernel and initial RAM disk. From the kickstart file, or from an option you enter manually to the installer, you can identify the location of the repository holding the RPM software packages. That location can be a local optical medium (CD, DVD), website (vita http), FTP site (via ftp), NFS share (via nfs), NFS ISO (nfsiso), or local disk (HD)\

5. **Modify installation with kickstart scripts**\
   Scripts included in a kickstart can run commands you choose before or after the installation to further configure the Linux system. Those commands can add users, change permissions, create files and directories, grab files over the network, or otherwise configure the installed system exactly as you specify.

Although installing Linux in enterprise environments is beyond the scope of this gitbook, I want you to understand the technologies that are available when you want to automate the Linux installation process. Here are some of those technologies available to use with RedHat Enterprise Linux, along with links to where you can find more information about them:

### Installation Server

If you set up an installation server, you don’t have to carry the software packages around to each machine where you install RHEL. Essentially, you copy all of the software packages from the RHEL installation medium to a Webserver, FTP server, or NFS server, and then point to the location of that server when you boot the installer. The RHEL 8 Installation Guide describes how to set up a local or network installation source [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_a\_standard\_rhel\_installation/index#prepareinstallation-source\_preparing-for-your-installation).

### PXE Server

If you have a computer with a Network Interface Card (NIC) that supports PXE booting (most do these days), you can set your computer’s BIOS to boot from that NIC. If you have set up a PXE server on that network, that server can present a menu to the computer containing entries to launch an installation process. The RHEL Installation Guide provides information on how to set up PXE servers for installation [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_a\_standard\_rhel\_installation/index#booting-theinstallation-using-pxe\_booting-the-installer).

### Kickstart Files

To automate an installation completely, you create what is called a kickstart file. By passing a kickstart file as a boot option to a Linux installer, you can provide answers to all of the installation questions that you would normally have to click through.&#x20;

When you install RHEL, a kickstart file containing answers to all installation questions for the installation you just did is contained in the `/root/anaconda-ks.cfg` file. You can present that file to your next installation to repeat the installation configuration, or use that file as a model for different installations.

See the Advanced RHEL Installation Guide for information on performing a kickstart installation [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_an\_advanced\_rhel\_installation/index/#performing\_an\_automated\_installation\_using\_kickstart), and creating your own kickstart files [here](https://access.redhat.com/documentation/en-us/red\_hat\_enterprise\_linux/8/html-single/performing\_an\_advanced\_rhel\_installation/index/#creating-kickstart-files\_installing-rhel-as-an-experienced-user).
