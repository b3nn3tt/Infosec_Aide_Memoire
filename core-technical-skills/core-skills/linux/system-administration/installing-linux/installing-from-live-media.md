# Installing from Live Media

Simplicity is the main advantage of installing from Live media. Essentially, you are just copying the kernel, applications, and settings from the ISO image to the hard disk. There are fewer decisions that you have to make to do this kind of installation, but you also don’t get to choose exactly which software packages to install. After the installation, you can add and remove packages as you please.

The first decisions that you must make about your Live media installation include where you want to install the system, and whether you want to keep existing operating systems around when your installation is done or not:

### **Single-Boot Computer**

The easiest way to install Linux is to not have to worry about other operating systems or data on the computer, and have Linux replace everything. When you are done, the computer boots up directly to your distribution of choice.

### **Multi-Boot Computer**

If you already have Windows installed on a computer and you don’t want to erase it, you can install your distribution along with Windows on that system. Then, at boot time, you can choose which operating system to start up. To be able to install Linux on a system with another operating system installed, you must have either extra disk space available (outside the Windows partition), or be able to shrink the Windows system to gain enough free space to install Linux.&#x20;

Because multi-boot computers are tedious to set up, and can risk damaging your already installed system, it is recommend that you install Linux on a separate computer, even an old used one, or as a virtual machine if your host computer has sufficient resources, as opposed to multi-booting.

### **Bare Metal or Virtual System**

The resulting installation can be installed to boot up directly from the computer hardware, or from within an existing operating system on the computer. If you have a computer that is running as a virtual host, you can install Linux on that system as a virtual guest.

Virtualisation host software includes the following options:

* **Linux, UNIX, Windows, and Mac OS**
  * [KVM](https://www.linux-kvm.org/page/Main\_Page)
  * [Xen](https://xenproject.org/)
  * [VirtualBox](https://www.virtualbox.org/)
* **Linux, Windows, and Mac OS**
  * [VMWare](https://www.vmware.com/uk.html)
* **Windows Only**
  * [Hyper-V](https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/about/)

You can use your chosen distribution live ISO image from disk, or burned to a DVD or USB, to start an installation from your chosen hypervisor host.

For the remainder of this section, we will use [Fedora](https://getfedora.org/) as our example distribution.

{% hint style="info" %}
_**Because the Fedora 30 installation is very similar to the Red Hat Enterprise Linux 8 installation described within this section, you can refer to this procedure if you want to go beyond the simple selections shown here (particularly in the area of storage configuration)**_
{% endhint %}

1. **Get Fedora**\
   Choose the Fedora Live media image that you want to use, download it to your local system, and burn it to an appropriate medium\

2. **Boot the Live image**\
   Insert the DVD or USB drive. When the BIOS screen appears, look for a message that tells you to press a particular function key (such as `F12`) to interrupt the boot process and select the boot medium. Select your burned DVD or USB drive, depending on which you have, and Fedora should come up and display the boot screen. When you see the boot screen, select `Start Fedora-Workstation-Live`\

3.  **Start the installation**\
    When the Welcome to Fedora screen appears, position your mouse over the Install to Hard Drive area and select it:\


    ![](<../../../../../.gitbook/assets/image (89).png>)

    \

4.  **Select the language**\
    When prompted, choose the language type that best suits you and select Next. You should then see the Installation summary screen:\


    <img src="../../../../../.gitbook/assets/image (180).png" alt="" data-size="original">


5. **Select Time & Date**\
   From the Time & Date screen, you can select your time zone either by clicking the map, or choosing the region and city from drop-down boxes. To set the date and time, if you have an Internet connection, you can select the `Network Time` button to turn it on, or you can select `OFF` and set the date and time manually from boxes on the bottom of the screen. Select Done in the upper-right corner when you are finished\

6. **Select the installation destination**\
   Available storage devices (such as your hard drive) are displayed, with your hard drive selected as the installation destination. If you want the installer to install Fedora automatically, reclaiming existing diskspace, make sure that your disk is selected (not a USB drive or other device connected to your computer), then make the following selections:\

   1. **Automatic . . .**\
      If there is enough available disk space on the selected disk drive, you can continue with the installation by selecting Continue. Otherwise, you need to reclaim disk space as follows:\
      \
      **`I would like to make additional space available. . .`**\
      \
      If you want to erase the hard drive completely, select this check box and click Continue. You can erase some or all of the partitions that currently contain data\

   2. **Reclaim Disk Space**\
      From this screen, you can select Delete All. Then select Reclaim Space. Partitioning is set up automatically and you are returned to the Installation Summary Screen\

7. **Select the keyboard**\
   You can just use the default English (U.S.) keyboard, or select `Keyboard` to choose a different keyboard layout\

8. **Begin installation**\
   Select Begin Installation to begin installing to you hard disk\

9. **Finish the configuration**\
   When the first part of the installation is complete, click Quit\

10. **Reboot**\
    Select the little on/off button from the menu on the top-right corner of the screen. When prompted, click the Restart button. Eject or remove the Live media when the system boot screen appears. The \
    computer should boot to your newly installed Fedora system. Note that **you may actually need to power off the computer** for it to boot back up.\

11. **Begin using Fedora**\
    A first boot screen appears at this point, allowing you to create a user account and password, among other things. You are automatically logged in as that user account when configuration is done. That account has `sudo` privileges, so you can immediately begin doing administrative tasks as needed\

12. **Get software updates**\
    To keep your system secure and up to date, one of the first tasks that you should do after installing Fedora is to get the latest versions of the software you just installed. If your computer has an Internet connection, you can simply open a Terminal as your new user and type `sudo dnf update` to download and update all of your packages from the Internet. If a new kernel is installed, you can reboot your computer to have that new kernel take effect.\


At this point, you can begin using the desktop.
