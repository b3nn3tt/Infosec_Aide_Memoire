# Going Beyond the Limitations of Software Center

As we just saw, Software Center is a pretty convenient way to install software. However, it has some clear limitations which will necessitate some alternative choices:

1. **More Repositories**\
   By default, enabled repositories ONLY contain open-source, freely distributable software. At some point you may want to install a piece of commercial software, or software that has particular licensing coinditions, that isn't included in the standard repos
2. **Beyond Desktop Applications**\
   For the most part, Software Center focusses on providing packages that sport a GUI. However, there are literally thousands of powerfull applications that are command-line only, and the only way to get those is to look outside of Software Center
3.  **Flexibility**\
    The Software Center prioritises ease of use, which means the intricacies of software installation are largely managed behind the scenes. Typically, when you install an application, numerous additional packages, or "dependencies," are installed alongside it. These can range from language packs and plugins to fonts and software libraries.\


    This process is automatic, with the Software Center handling everything quietly in the background. However, this simplicity can sometimes lead to complications. For instance, if an application you're installing requires a newer version of a package that's already on your system, the Software Center will upgrade that package. This can inadvertently cause issues if other applications on your system rely on the older version of the upgraded package, potentially resulting in software conflicts or broken applications.\


    For those who prefer to manage the details of package installations and dependencies, command-line tools like **`apt`** and **`dpkg`** offer greater transparency and control, albeit with a slightly steeper learning curve.
4. **Software Validation**\
   Utilising tools such as **`apt`**, it's possible to verify the integrity of signed packages, ensuring they haven't been altered before you install them. This also applies to checking if any components of a package have been modified post-installation. These tools provide an additional security measure by confirming that packages remain in their original, untampered state from the time they were signed to the moment they're running on your system.
5. **Managing Software**\
   While the Software Center is suitable for installing desktop applications on an individual system, it's not designed for handling software deployment across multiple systems. For larger scale management, there are other tools that build upon the 'apt' system to facilitate this kind of software administration. These tools provide a more robust and scalable solution for managing installations and updates across numerous machines.

{% hint style="info" %}
**Linux Software Packaging 101: A Brief History**

In the early days of Linux, adding software typically meant grabbing the source code from the developers (there was no github back then either...), compiling it into executable binaries, and then installing it on your system. Occasionally, if you were lucky, you might find the software pre-compiled to run on your machine.

\
Software often came in the form of a **tarball** – a bundled file collection not _too dissimilar_ to a zip file, including executables, documentation, config files, and libraries, designed for easy storage or distribution. Installing from a tarball would scatter files across various directories on your Linux system such as **`/usr/share/man`**, **`/etc`**, **`/bin`**, and **`/lib`**.&#x20;

\
Despite tarballs making it straightforward to bundle and deploy software, this installation approach presented challenges., such as ensuring all dependencies were satisfied, updating the software at a later time, or even accounting for what software was currently installed on the system without trawling through the file system manually identifying what was present - in short, **a pain in the a$#e!**\
\
To overcome said limitations, a more comprehensive packaging system was devised. With only a handful of exceptions (as always with Linux...), the majority of distros support one of two packaging formats: **DEB** (for Debian, Ubuntu, Mint, etc...) and **RPM** (RHEL, Fedora, Suse, etc...). Think of these packages as "all in one" solutions for easily installing new software.

\
For the remainder of this aide memoire, ill stick mostly to the .deb packages as I use Debian, Ubuntu, and Kali all the time so its what I know best, but in truth, working with .rpm isnt all that different (usually just syntax) so you'll still be able to apply what you see here.
{% endhint %}

