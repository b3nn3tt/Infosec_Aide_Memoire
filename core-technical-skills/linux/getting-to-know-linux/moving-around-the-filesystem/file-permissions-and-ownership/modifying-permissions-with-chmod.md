# Modifying Permissions with chmod

If you own a file, or you have administrative privileges, you can use the `chmod` command to change the permission on it as you please. There are two methods for modifying permissions:

* Numeric
* Letters

## Numeric Modification

Each permission \(read, write, and execute\) is assigned a number:

* r = 4
* w = 2
* x = 1

You use each set of users \(owner, group owner, and anyone else\) total numeric value to establish the permissions for the file. For example, to make permissions wide open for yourself as owner, you would set the first number to 7 \(4 + 2 + 1\), and then you would give the group and others read-only permission by setting both the second and third numbers to 4 \(4 + 0 + 0\), so that the final number is **744**.

Any combination of permissions can result from 0 \(no permission\) through 7\(full permission\).

| Command | Resulting Permissions |
| :--- | :--- |
| `chmod 777 example_file` | `RWX | RWX | RWX` |
| `chmod 755 example_file` | `RWX | R-X | R-X` |
| `chmod 644 example_file` | `RW- | R-- | R--` |
| `chmod 000 example_file` | `--- | --- | ---` |

The `chmod` command can also be used **recursively**. For example, suppose that you wanted to give an entire directory structure `755` permission \(`RWX | R-X | R-X`\), starting at the `$HOME/myapps` directory. To do that, you could use the `-R` option, as follows:

```text
chmod -R 755 $HOME/myapps
```

All files and directories below \(and including\) the `$HOME/myapps` directory will have `755` permissions set. Because the numbers approach to setting permission changes all permission bits at once, it’s more common to use letters to change permission bits recursively over a large set of files.

## Letter Modification

You can turn file permissions on and off using plus \(`+`\) and minus \(`–`\) signs, respectively, along with letters to indicate what changes and for whom. Using letters, for each file you can change permission for the user \(`u`\), group \(`g`\), other \(`o`\), and all users \(`a`\). What you would change includes the read \(`r`\), write \(`w`\), and execute \(`x`\) bits.

For example, let's start with a file that has all permissions open \(`777`, or `RWX | RWX | RWX`\). Run the following `chmod` commands using minus sign options. The resulting permissions are shown to the right of each command.

| Original Permissions | Command | Resulting Permissions |
| :--- | :--- | :--- |
| `RWX | RWX | RWX` | `chmod a-w example` | `R-X | R-X | R-X` |
| `RWX | RWX | RWX` | `chmod o-x example` | `RWX | RWX | RW-` |
| `RWX | RWX | RWX` | `chmod go-rwx example` | `RWX | --- | ---` |

As you can see, you can change a single property of the permissions without having to specify all 3 sets. This makes adding or stripping permissions from a particular set much easier, and the remaining sets are left intact. For example, suppose that you want to remove write permission for **other** without changing any other permission bits on a set of files and directories. You could do the following:

```text
chmod -R o-w $HOME/myapps
```

This example recursively removes write permissions for **other** on any files and directories below the `myapps` directory. If you had used numbers such as `644`, execute permission would be turned off for directories; using `755`, execute permission would be turned on for regular files. Using `o-w`, only one bit is turned off and all other bits are left alone.

