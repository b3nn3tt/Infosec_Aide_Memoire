# Modifying Permissions with chmod

If you're the owner of a file, or have admin powers, you can freely tinker with its permissions using the `chmod` command. There are two ways to tweak these permissions:

* Numeric
* Letters

##

## Numeric Modification

Each permission (read, write, and execute) is assigned a numerical value:

* `r = 4`
* `w = 2`
* `x = 1`

To define file permissions, you assign a numeric value to each group of users (owner, group owner, and others). For instance, if you want to grant full access to yourself as the owner, you'd set the first number to **7** (4 + 2 + 1). Then, for the group and others, if you want to allow **read-only access**, you'd set both the second and third numbers to **4** (4 + 0 + 0), making the final number **744**.

You can use any combination of permissions, ranging from **0** (no access) to **7** (complete access):

| Command                  | Resulting Permissions |
| ------------------------ | --------------------- |
| `chmod 777 example_file` | `RWX \| RWX \| RWX`   |
| `chmod 755 example_file` | `RWX \| R-X \| R-X`   |
| `chmod 644 example_file` | `RW- \| R-- \| R--`   |
| `chmod 000 example_file` | `--- \| --- \| ---`   |

You can also use the chmod command **recursively**. For instance, if you want to grant **755** permissions (**RWX | R-X | R-X**) to an entire directory structure starting from `$HOME/myapps`, you can utilize the `-R` option, like this:

```
chmod -R 755 $HOME/myapps
```

Now, **all files and directories** within (and including) the `$HOME/myapps` directory will have **755** permissions applied.&#x20;

{% hint style="info" %}
When you need to change permission bits recursively for a large group of files, it's more common to use letters instead of the numerical approach, as it allows you to modify permission bits individually.
{% endhint %}

##

## Letter Modification

You can enable or disable file permissions using plus (`+`) and minus (`–`) signs, along with letters to specify what changes, and for whom. When using letters, you can alter permissions for the user (`u`), group (`g`), other (`o`), and all users (`a`). The changes include read (`r`), write (`w`), and execute (`x`) bits.

For instance, let's begin with a file that has all permissions granted (**777**, or **RWX | RWX | RWX**). Execute the following `chmod` commands using minus options. The resulting permissions are displayed to the right of each command:

| Original Permissions | Command                | Resulting Permissions |
| -------------------- | ---------------------- | --------------------- |
| `RWX \| RWX \| RWX`  | `chmod a-w example`    | `R-X \| R-X \| R-X`   |
| `RWX \| RWX \| RWX`  | `chmod o-x example`    | `RWX \| RWX \| RW-`   |
| `RWX \| RWX \| RWX`  | `chmod go-rwx example` | `RWX \| --- \| ---`   |

Indeed, you can modify a single aspect of the permissions without needing to specify all three sets. This simplifies the process of adding or removing permissions from a specific set, leaving the other sets unaffected. For instance, if you wish to eliminate write permission for others without altering any other permission bits for a group of files and directories, you could execute the following:

```
chmod -R o-w $HOME/myapps
```

This example recursively removes write permissions for **other** on any files and directories below the `myapps` directory. If you had used numbers such as `644`, execute permission would be turned off for directories; using `755`, execute permission would be turned on for regular files. Using `o-w`, only one bit is turned off and all other bits are left alone.
