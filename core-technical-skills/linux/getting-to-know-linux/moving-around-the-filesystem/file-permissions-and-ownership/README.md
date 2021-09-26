# File Permissions and Ownership

After you’ve worked with Linux for a while, you are almost sure to get a "_Permission Denied_" message. Permissions associated with files and directories in Linux were designed to keep users from accessing other users’ private files, and to protect important system files.

The nine bits assigned to each file for permissions define the access that you and others have to your file. Permission bits for a regular file appear as `-rwxrwxrwx`. Those bits are used to define who can read, write, or execute the file.

Of the nine-bit permissions: 

* The first three bits apply to the **owner’s** permission
* The next three apply to the **group** assigned to the file
* The last three apply to all **others**

The `r` stands for **read**, the `w` stands for **write**, and the `x` stands for **execute** permissions. If a dash appears instead of the letter, it means that permission is turned off for that associated read, write, or execute bit. Because files and directories are different types of elements, read, write, and execute permissions on files and directories mean different things. The following table explains what you can do with each of them:

| Permission | File |
| :--- | :--- |
| `READ` | View what's in the file |
| `WRITE` | Change the files contents, rename it, or delete it |
| `EXECUTE` | Run the file as a program |

As noted earlier, you can see the permission for any specified file or directory by typing the `ls -ld` command. The named file or directory appears as those shown in this example:











