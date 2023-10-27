# wget

The [wget](https://www.gnu.org/software/wget/) command, which we will use extensively throughout this aide-memoire, downloads files using the HTTP/HTTPS and FTP protocols. The example below shows the use of `wget` along with the `-O` switch to save the destination file with a different name on the local machine:

```
wget -O report_wget.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf
```

![Downloading a file with wget, renaming the local copy](<../../../../../../.gitbook/assets/image (179).png>)

##

## &#x20;Additional Options

wget has some other handy options that you should be familiar with.&#x20;

###

### Specifying an Output Directory

We can specify a directory to download a file to with the `-P` option:

```
wget -P /mnt/iso http://mirrors.mit.edu/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1804.iso
```

###

### Download Multiple Files

If you want to download multiple files at once, use the `-i` option, followed by the path to a local or external file containing a list of the URLs to be downloaded. Each URL needs to be on a separate line.

The following example shows how to download the Arch Linux, Debian, and Fedora iso files using the URLs specified in the `linux-distros.txt` file:

```
wget -i linux-distros.txt
```

```
http://mirrors.edge.kernel.org/archlinux/iso/2018.06.01/archlinux-2018.06.01-x86_64.iso
https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-9.4.0-amd64-netinst.iso
https://download.fedoraproject.org/pub/fedora/linux/releases/28/Server/x86_64/iso/Fedora-Server-dvd-x86_64-28-1.1.iso
```

###

### Resume a Download

We can also resume a download that has dropped off with `-c`:

```
wget -c http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso
```

{% hint style="info" %}
&#x20;If the remote server does not support resuming downloads, `wget` will start the download from the beginning and overwrite the existing file.
{% endhint %}

####

### Download in the Background

We can also run downloads in the background with the `-b` option:

```
wget -b https://download.opensuse.org/tumbleweed/iso/openSUSE-Tumbleweed-DVD-x86_64-Current.iso
```

{% hint style="info" %}
&#x20;By default, the output is redirected to `wget-log` file in the current directory. To watch the status of the download, use the [`tail`](https://linuxize.com/post/linux-head-command/) command:

`$ tail -f wget-log`
{% endhint %}

####

### Change the User-Agent String

We can also manually change the User-Agent string so `wget` can appear as any browser when downloading a file via the `--user-agent=` option:

```
wget --user-agent="Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0" http://wget-forbidden.com/
```

####

### Download a Local Copy of a Website

To create a mirror of a website with `wget`, use the `-m` option. This will create a complete local copy of the website by following and downloading all internal links as well as the website resources (JavaScript, CSS, Images):

```
wget -m https://example.com
```

If you want to use the downloaded website for local browsing, you will need to pass a few extra arguments to the command above:

```
wget -m -k -p https://example.com
```

The `-k` option will cause `wget` to convert the links in the downloaded documents to make them suitable for local viewing. The `-p` option will tell `wget` to download all necessary files for displaying the HTML page.

####

### Skipping the SSL Certificate Check

&#x20;If you want to download a file over HTTPS from a host that has an invalid SSL certificate, use the `--no-check-certificate` option:

```
wget --no-check-certificate https://domain-with-invalid-ss.com
```

####

### Download to Standard Output (STDOUT)

In the following example, `wget` will quietly (`-q`) download and output the latest WordPress version to STDOUT(`-O -`) and pipe it to the `tar` utility, which will extract the archive to the `/var/www` directory.

```
wget -q -O - "http://wordpress.org/latest.tar.gz" | tar -xzf - -C /var/www
```





