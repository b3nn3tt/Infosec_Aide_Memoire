# Installing from Live Media

The charm of installing from Live media lies in its simplicity. In essence, you're just transferring the kernel, apps, and configurations straight from the ISO image to the hard disk. It's a very **decision-light** procedure – fewer forks in the road to ponder over. However, this method doesn't let you handpick the specific software packages during the initial setup. Of course, you've got full freedom to tinker with packages post-installation.

When you're getting down to the nitty-gritty with a Live media installation, the initial choices you face are critical. You need to decide on the destination for your Linux system and whether you're going to let your new Linux setup fly solo on your hard drive, or if it’s going to share space with existing operating systems. That leads us nicely into...



## **Single-Boot Computer**

The most straightforward path to installing Linux is to go for a clean slate approach, letting Linux take over the entire computer. This way, you don't have to juggle with other operating systems or existing data. Once the installation wraps up, you'll switch on your computer and be greeted directly by your chosen Linux distribution, neat and tidy.

###

## **Multi-Boot Computer**

Want to keep Windows but fancy a slice of Linux life on the side? You can set your system to be a multi-boot machine. This means when you power up, you'll have the choice of operating system – a bit like choosing between tea and coffee in the morning.

To make room for Linux, you'll need some unallocated space on your disk – either by having a spare bit of the drive ready or by shrinking the Windows partition to free up some room.

#### <mark style="color:red;">A word of caution!</mark>

Multi-boot setups can be fiddly, and there's a small risk of upsetting your existing Windows installation. If you want to play it safe, consider giving Linux its own playground – an older computer will do just fine, or tuck it into a virtual machine if your main rig has got the muscle for it. That way, you get the best of both worlds without the partitioning palaver.



## **Bare Metal or Virtual System**

The beauty of the installation you end up with is its versatility. You can set it up to boot straight from your computer's hardware, giving Linux centre stage, or you can have it nestled snugly within an already-running operating system – a bit like having a cosy flat within a bustling city building.

And if you've got a machine that's acting the part of a virtual host, you're in luck. You can welcome Linux aboard as a virtual guest without much fuss.

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



## Installation Walkthrough

#### For the remainder of this section, we will use [Fedora](https://getfedora.org/) as our example distribution



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


At this point, you can begin using the desktop. Simples!
