# Modifying Default Permissions with umask

When you create a **file** as a **regular user**, it’s given permission `RW- | RW- | R--` **** by default. When you create a **directory**, it's given permission `RWX | RWX | R-X` **by default**. For the root user, file and directory permission are `RW- | R-- | R--` **and** `RWX | R-X | R-X`, respectively. These default values are determined by the value of `umask`. Enter `umask` to see what your default value is.&#x20;

For example:

```
umask
```

![Default permission configuration example](<../../../../../.gitbook/assets/image (5).png>)

If you ignore the leading zero for the moment, the `umask` value masks what is considered to be fully opened permissions for a file `666` or a directory `777`. The `umask` value of `002` results in permissions for a directory of `775` (`RWX | RWX | R-X`). That same `umask` results in permissions for a file of `644` (`RW- | RW- | R--`). **Execute permissions are off by default for regular files**.

To change your `umask` value temporarily, run the `umask` command. Then, try creating some files and directories to see how the `umask` value affects how permissions are set. Here are some examples:

![Examples of different umask values](<../../../../../.gitbook/assets/image (26).png>)

If you want to change your `umask` value permanently, add a `umask` command to the `.bashrc` file in your home directory.
