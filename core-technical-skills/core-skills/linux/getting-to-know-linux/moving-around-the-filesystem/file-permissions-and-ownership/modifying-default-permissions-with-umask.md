# Modifying Default Permissions with umask

When you, as a **regular user**, create a **file**, it's given a set of default permissions of **664**, while **directories** get **775**. For the mighty root user, **file** permissions default to **644** and **directories** to **755**. These defaults are influenced by the **umask value**. You can check your default umask value by typing `umask` like this:

```
umask
```

![Default permission configuration example](<../../../../../../.gitbook/assets/image (134).png>)

If you ignore the leading zero for the moment, your **umask value** is essentially a mask that hides what would otherwise be completely open permissions for a file (**666**) or a directory (**777**). A umask value of `002` means that directory permissions become **775**, and file permissions become **644**, **assuming execute permissions are disabled by default for regular files as standard**.&#x20;

You can alter your umask value temporarily by using the `umask` command. Afterward, you can create files and directories to observe how the umask value influences permission settings.

Here are some examples:

![Examples of different umask values](<../../../../../../.gitbook/assets/image (135).png>)

If you want to change your `umask` value permanently, add a `umask` command to the `.bashrc` file in your home directory.
