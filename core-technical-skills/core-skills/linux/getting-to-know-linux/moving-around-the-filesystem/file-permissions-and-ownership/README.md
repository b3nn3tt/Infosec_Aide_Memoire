# File Permissions and Ownership

After you’ve worked with Linux for a while, it's almost inevitable that you'll bump into a "Permission Denied" message at some point. It's Linux's polite way of keeping order – preventing you from peeping into someone else's private files or inadvertently meddling with crucial system files.

Every file and directory has a set of nine permission bits, looking something like `-rwxrwxrwx`. These little guys dictate **who** can do **what** – read, write, or execute a file.

Here's a breakdown:

* The first three bits apply to the **owner’s** permission
* The next three apply to the **group** assigned to the file
* The last three apply to **everyone else**

In this permission [alphabetti-spaghetti](https://www.heinz.co.uk/pasta/alphabettinumberetti/product/100185200055/alphabetti), the `r` stands for **read**, the `w` stands for **write**, and the `x` stands for **execute** permissions. If a dash appears in place of a letter, it means that permission is turned off for that associated read, write, or execution bit.

But here’s the twist: files and directories might be different beasts, but **they share the same permission bits**. The only difference is how these permissions play out for each. Let’s break down what each permission lets you do:

| Permission | File                                               | Folder                                                        |
| ---------- | -------------------------------------------------- | ------------------------------------------------------------- |
| `READ`     | View what's in the file                            | Permits listing the directory's contents                      |
| `WRITE`    | Change the files contents, rename it, or delete it | Allows creating, deleting, or renaming files in the directory |
| `EXECUTE`  | Run the file as a program                          | Permits accessing the directory and its contents              |
