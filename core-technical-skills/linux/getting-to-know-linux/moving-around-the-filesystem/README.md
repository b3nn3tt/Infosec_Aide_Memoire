# Moving Around the Filesystem

The Linux filesystem \(LFS\) is the structure in which all of the information on your computer is stored. In fact, one of the defining properties of the UNIX systems on which Linux is based is that nearly everything you need to identify on your system \(data, commands, symbolic links, devices, and directories\) is represented by items in the filesystems. Knowing where things are, and understanding how to get around the filesystem from the shell, are critical skills in Linux.

In Linux, files are organized within a hierarchy of directories. Each directory can contain files as well as other directories. You can refer to any file or directory using either a **full path** \(for example, `/home/joe/myfile.txt`\) or a **relative path** \(for example, if `/home/joe` were your current directory, you could simply refer to the file as `myfile.txt`\).

If you were to map out the files and directories in Linux, it would look like an upside-down tree. At the top is the **root directory** \(not to be confused with the root user\), which is represented by a single slash `/`. Below that is a set of common directories in the Linux system, such as `bin`, `dev`, `home`, `lib`, and `tmp`, to name a few. Each of those directories, as well as directories added to the root directory, can contain subdirectories. The following diagram illustrates how the Linux filesystem is organized as a hierarchy:

![Visual depiction of the LFS](../../../../.gitbook/assets/image%20%2821%29.png)

To demonstrate how directories are connected, the figure shows a `/home` directory that contains a subdirectory for the user joe. Within the joe directory are Desktop, Documents, and other subdirectories. To refer to a file called `memo1.doc` in the memos directory, you can type the full path of `/home/joe/Documents/memos/memo1.doc`. If your current directory is `/home/joe/`, refer to the file as `Documents/memos/memo1.doc`.

Some of these Linux directories may interest you:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Directory</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>/bin</code>
      </td>
      <td style="text-align:left">Contains common Linux user commands, such as <code>ls</code>, <code>sort</code>, <code>date</code>,
        and <code>chmod</code>. <code>/boot</code> Has the bootable Linux kernel,
        initial RAM disk, and boot loader configuration files (GRUB)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/dev</code>
      </td>
      <td style="text-align:left">Contains files representing access points to devices on your systems.
        These include terminal devices (tty<em>), hard disks (hd</em> or sd<em>), RAM (ram</em>),
        and CD-ROM(cd*). Users can access these devices directly through these
        device files; however, applications often hide the actual device names
        to end users</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/etc</code>
      </td>
      <td style="text-align:left">Contains administrative configuration files. Most of these files are plain-text
        files that, given the user has proper permission, can be edited with any
        text editor</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/home</code>
      </td>
      <td style="text-align:left">Contains directories assigned to each regular user with a login account.
        The root user is an exception, using /root as his or her home directory
        (see below)</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/media</code>
      </td>
      <td style="text-align:left">Provides a standard location for automounting devices (removable media
        in particular). If the medium has a volume name, that name is typically
        used as the mountpoint. For example, a USB drive with a volume name of
        myusb would be mounted on <code>/media/myusb</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/lib</code>
      </td>
      <td style="text-align:left">Contains shared libraries needed by applications in <code>/bin</code> and <code>/sbin</code> to
        boot the system</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/mnt</code>
      </td>
      <td style="text-align:left">A common mount point for many devices before it was supplanted by the
        standard <code>/media</code> directory. Some bootable Linux systems still
        use this directory to mount hard disk partitions and remote filesystems.
        Many people still use this directory to temporarily mount local or remote
        filesystems, which are not mounted permanently.</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/misc</code>
      </td>
      <td style="text-align:left">A directory sometimes used to automount filesystems upon request</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/opt</code>
      </td>
      <td style="text-align:left">Directory structure available to store add-on application software</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/proc</code>
      </td>
      <td style="text-align:left">Contains information about system resources</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/root</code>
      </td>
      <td style="text-align:left">Represents the root user&#x2019;s home directory. The home directory for
        root does not reside beneath <code>/home</code> for security reasons</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/sbin</code>
      </td>
      <td style="text-align:left">Contains administrative commands and daemon processes</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/sys</code>
      </td>
      <td style="text-align:left">Contains parameters for such things as tuning block storage and managing
        cgroups</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/tmp</code>
      </td>
      <td style="text-align:left">Contains temporary files used by applications</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/usr</code>
      </td>
      <td style="text-align:left">
        <p>Contains user documentation, games, graphical files (X11), libraries (lib),
          and a variety of other commands and files that are not needed during the
          boot process. The <code>/usr</code> directory is meant for files that don&#x2019;t
          change after installation.</p>
        <p></p>
        <p>In theory, <code>/usr</code> could be mounted read-only</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>/var</code>
      </td>
      <td style="text-align:left">
        <p>Contains directories of data used by various applications. In particular,
          this is where you would place files that you share as an FTP server (<code>/var/ftp</code>)
          or a webserver (<code>/var/www</code>). It also contains all system log
          files (<code>/var/log</code>) and spool files in<code>/var/spool</code>(such
          as mail, cups, and news).</p>
        <p></p>
        <p>The<code>/var</code> directory contains directories and files that are
          meant to change often. On server computers, it is common to create the <code>/var</code> directory
          as a <b>separate filesystem</b>, using a filesystem type that can be easily
          expanded</p>
      </td>
    </tr>
  </tbody>
</table>

