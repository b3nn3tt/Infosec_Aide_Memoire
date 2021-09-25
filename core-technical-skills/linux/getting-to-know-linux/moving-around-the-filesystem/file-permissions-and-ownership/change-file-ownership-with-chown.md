# Change File Ownership with chown

If you want to change the owner of a file or directory, you can use the `chown` command, the syntax for which is as follows:

```text
chown DESIRED_OWNER PATH/TO/FILE
```

As a regular user, _**you cannot change ownership of files or directories to have them belong to another user**_. You can however change ownership as the **root** user. For example, suppose that you created a file called `memo.txt` in the user joe’s home directory while you were root user. Here’s how you could change it to be owned by joe:

```text
chown joe /home/joe/memo.txt
```

This will change ownership of `memo.txt` to joe. However, this does not change the group owner, merely the user owner. If you wanted to change the group owner at the same time, you could have entered:

```text
chown joe:joe /home/joe/memo.txt
```

Now, the file is also owned by the group joe.

{% hint style="info" %}
When a new user is created, it is typical for a group to be created of the same name. This is because Linux requires users to be a member of at least one group, referred to as their primary group, as part of its security and access control model.
{% endhint %}

The `chown` command can be use recursively as well. Using the recursive option \(`-R`\) is helpful if you need to change a whole directory structure to ownership by a particular user. For example, if you inserted a USB drive, which is mounted on the `/media/myusb` directory, and you wanted to give full ownership of the contents of that drive to the user joe, you could enter the following:

```text
chown -R joe:joe /media/myusb
```





