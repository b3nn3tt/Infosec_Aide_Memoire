# Change File Ownership with chown

If you want to change the owner of a file or directory, you can use the `chown` command. The syntax is as follows:

```
chown DESIRED_OWNER PATH/TO/FILE
```

It is important to understand that as a **regular user**, <mark style="color:red;">**you cannot change ownership of files or directories to have them belong to another user**</mark>. However, <mark style="color:green;">**the root account can**</mark>. Consider the following example.

Let's suppose that you created a file called `memo.txt` in the user chris’s home directory **while you were root user**. Here’s how you, **as root**, could change it to be owned by chris:

```
chown chris /home/chris/memo.txt
```

This will change ownership of `memo.txt` to chris. However, this does not change the group owner, merely the user owner. If you wanted to change the group owner at the same time, you could have entered:

```
chown chris:chris /home/chris/memo.txt
```

Now, the file is also owned by the group joe.

{% hint style="info" %}
When a new user is created, it is typical for a group to be created of the same name. This is because Linux requires users to be a member of at least one group, referred to as their primary group, as part of its security and access control model.
{% endhint %}

The `chown` command can also be employed recursively with the help of the `-R` option. This is particularly useful when you need to modify the ownership of an entire directory structure to be owned by a specific user. For instance, if you've connected a USB drive, mounted it on the `/media/myusb` directory, and wish to grant complete ownership of the drive's contents to the user chris, you can execute the following command:

```
chown -R chris:chris /media/myusb
```
