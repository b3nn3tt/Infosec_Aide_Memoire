# find

The `find` command is the best option for searching your filesystem for files based on a variety of attributes. After files are found, you can act on those files \(using the `-exec` or `-okay` options\), running any commands you want on them.

When you run `find`, it searches your filesystem in live time, which causes it to run slower than `locate`, but it gives you an up-to-the-moment view of the files on your Linux system. However, you can also tell find to start at a particular point in the filesystem so that the search can go faster by limiting the area being searched.

Nearly any file attribute that you can think of can be used as a search option. You can search for file names, ownership, permission, size, modification times, and other attributes. You can even use combinations of attributes.

## General Syntax

The general syntax for the `find` command is as follows:

```text
find [options] [path...] [expression]
```

* The `options` attribute controls the treatment of the symbolic links, debugging options, and optimization method
* The `path...` attribute defines the starting directory or directories where find will search the files
* The `expression` attribute is made up of options, search patterns, and actions separated by operators

{% hint style="info" %}
As a regular user, `find` does not give you special permission to identify files. This means that files that are beyond your level of privilege will not be returned when running your search. Consequently, `find` produces a bunch of error messages.

However, when run with elevated privileges, `find` will search the entirety of the file system if you direct it to; it is not limited in the same way we saw with `locate`.
{% endhint %}

Let’s take a look at the following example:

```text
find -L /var/www -name "*.js"
```

* The option `-L` \(options\) tells the `find` command to follow symbolic links
* The `/var/www` \(path…\) specifies the directory that will be searched
* The \(expression\) `-name "*.js` tells `find` to search files ending with `.js` \(JavaScript files\)

## Additional Options

### Find Files by Name

Finding files by name is probably the most common use of the `find` command. To find a file by its name, use the `-name` option followed by the name of the file you are searching for.

For example, to search for a file named `document.pdf` in the `/home/example` directory, you would use the following command:

```text
find /home/example-type f -name document.pdf
```

To run a case-insensitive search, change the `-name` option with `-iname`:

```text
find /home/example -type f -iname document.pdf
```

The command above will match “Document.pdf”, “DOCUMENT.pdf” ..etc.

### 

### Find Files by Type

Sometimes you might need to search for specific file types such as regular files, directories, or symlinks. In Linux, everything is a file.

To search for files based on their type, use the `-type` option, along with one of the following descriptors to specify the file type:

* `f`: a regular file
* `d`: directory
* `l`: [symbolic link](https://linuxize.com/post/how-to-create-symbolic-links-in-linux-using-the-ln-command/)
* `c`: character devices
* `b`: block devices
* `p`: named pipe \(FIFO\)
* `s`: socket

For instance, to find all directories in the current working directory , you would use:

```text
find . -type d
```

The common example would be to recursively change the website file permissions to `644` and directory permissions to `755` using the [`chmod`](https://linuxize.com/post/chmod-command-in-linux/) command:

```text
find /var/www/my_website -type d -exec chmod 0755 {} \;
find /var/www/my_website -type f -exec chmod 0644 {} \;
```

### 

### Find Files by Size

To find files based on the file size, pass the `-size` parameter along with the size criteria. You can use the following suffixes to specify the file size:

* `b`: 512-byte blocks \(default\)
* `c`: bytes
* `w`: two-byte words
* `k`: Kilobytes
* `M`: Megabytes
* `G`: Gigabytes

The following command will find all files of exactly `1024` bytes inside the `/tmp` directory:

```text
find /tmp -type f -size 1024c
```

The `find` command also allows you to search for files that are greater or less than a specified size.

In the following example, we search for all files less than `1MB` inside the current working directory. Notice the minus `-` symbol before the size value:

```text
find . -type f -size -1M
```

If you want to search for files with a size greater than `1MB`, then you need to use the plus `+` symbol:

```text
find . -type f -size +1M
```

You can even search for files within a size range. The following command will find all files between `1` and `2MB`:

```text
find . -type f -size +1M -size 21M
```



### Find Files by Modification Date <a id="find-files-by-modification-date"></a>

The `find` command can also search for files based on their last modification, access, or change time. Much the same as when searching by size, you can use the plus and minus symbols for “greater than” or “less than”.

Let’s say that a few days ago, you modified one of the dovecot configuration files, but you forgot which one. You can easily filter all files under the `/etc/dovecot/conf.d` directory that ends with `.conf` and has been modified in the last five days:

```text
find /etc/dovecot/conf.d -name "*.conf" -mtime 5
```

Here is another example of filtering files based on the modification date using the `-daystart` option. The command below will list all files in the `/home` directory that were modified `30` or more days ago:

```text
find /home -mtime +30 -daystart
```



### Find Files by Permissions <a id="find-files-by-permissions"></a>

The `-perm` option allows you to search for files based on the file permissions.

For example, to find all files with permissions of exactly `775` inside the `/var/www/html` directory, you would use:

```text
find /var/www/html -perm 644
```

You can prefix the numeric mode with minus `-` or slash `/`.

When slash `/` is used as the prefix, then at least one category \(user, group, or others\) must have at least the respective bits set for a file to match.

Consider the following example command:

```text
find . -perm /444
```

The above command will match all the files with read permissions set for either user, group, or others.

If minus `-` is used as the prefix, then for the file to match, at least the specified bits must be set. The following command will search for files that have read and write permission for the owner and group and are readable by other users:

```text
find . -perm -664
```



### Find Files by Owner <a id="find-files-by-owner"></a>

To find files owned by a particular user or group, use the `-user` and `-group` options.

For example, to search for all files and directories owned by the user `example`, you would run:

```text
find / -user example
```

Here is a real-world example. Let’s say you want to find all files owned by the user `www-data` and change the ownership of the matched files from `www-data` to `nginx`:

```text
find / -user www-data -type f  -exec chown nginx {} \;
```

###  <a id="find-and-delete-files"></a>

### Find and Delete Files <a id="find-and-delete-files"></a>

To delete all matching files, append the `-delete` option to the end of the match expression.

Ensure you are using this option only when you are confident that the result matches the files you want to delete. It is always a good idea to print the matched files before using the `-delete` option.

For example, to delete all files ending with `.temp` from the `/var/log/`, you would use:

```text
find /var/log/ -name `*.temp` -delete
```

{% hint style="info" %}
Use the `-delete` option with **extreme caution**. The `find` command is evaluated as an expression and if you add the `-delete` option first, the command will delete everything below the starting points you specified.
{% endhint %}

When it comes to directories, `find` can delete only empty directories, same as [`rmdir`](https://linuxize.com/post/remove-directory-linux/) .





























