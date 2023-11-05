# Account Administration

A computer is pretty useless without accounts. So, we need to learn how to administer user accounts, both privileged and non-privileged, as well as **service accounts**.

To begin with, we need to understand a very important file; **`/etc/passwd`**.

###

## Understanding /etc/passwd

The **`/etc/passwd`** file is basically a roster of all the user accounts on the system. It's a simple text file that gives out a bunch of details for each account, such as your user ID, the group ID you belong to, where your home directory is, which shell you use, and a few other bits and bobs. Pretty much anyone can read this file since it's used by various system commands to match user IDs with their usernames. But when it comes to writing to this file, that's kept under lock and key, with only root having the authority to make any changes.

The **`/etc/passwd`** file contains one entry per line for each account present on the system. All fields are separated by a colon (**`:`**) symbol. There are seven fields in total, which generally appears as follows:

![Example /etc/passwd entry](<../../../../../.gitbook/assets/image (92).png>)

1. **Username**\
   It is used when user logs in. It should be between 1 and 32 characters in length\

2. **Password**\
   An **`x`** character indicates that encrypted password is stored in another file; the **`/etc/shadow`** file. Please note that you need to use the `passwd` command to change an account passed to ensure that the password typed at the CLI is hashed correctly. _We will revisit this mechanism later_...\

3. **User ID (UID)**\
   Each user must be assigned a user ID (UID). **UID 0** (zero) is reserved for **`root`** and **UIDs 1-99** are reserved for other predefined accounts. Further UID 100-999 are reserved by system for administrative and system accounts/groups\

4. **Group ID (GID)**\
   The primary group ID, stored in **`/etc/group`** file\

5. **User ID Info (GECOS)**\
   The comment field. It allow you to add extra information about the users such as user’s full name, phone number etc. This field use by **`finger`** command\

6. **Home directory**\
   The absolute path to the directory the user will be in when they log in. If this directory does not exists then users directory becomes **`/`**\

7. **Command/shell**\
   The absolute path of a command or shell (typically **`/bin/bash`**). Please note that it does not have to be a shell. For example, sysadmin can use the **`nologin`** shell, which acts as a replacement shell for the user accounts. If shell set to **`/sbin/nologin`** and the user tries to log in to the Linux system directly, the **`/sbin/nologin`** shell closes the connection
