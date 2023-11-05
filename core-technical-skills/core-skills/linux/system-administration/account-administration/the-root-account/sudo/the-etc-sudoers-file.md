# The /etc/sudoers File

The easiest thing to do is to look at the **`/etc/sudoers`** file to see what is happening. For this example, we will look at a default installation of Ubuntu:

```
sudo nano /etc/sudoers
```

![A default /etc/sudoers file in Ubuntu](<../../../../../../../.gitbook/assets/image (33).png>)

Let's take a look at the various sections in closer details...

## Default Lines

* **`Defaults env_reset`** resets the terminal environment to remove any user variables. This is a safety measure used to clear potentially harmful environmental variables from the **`sudo`** session\

* **`Defaults mail_badpass`** tells the system to mail notices of bad **`sudo`** password attempts to the configured **`mailto`** user. By default, this is the root account\

* **`Defaults secure_path=`** specifies the PATH (the places in the filesystem the operating system will look for applications) that will be used for **`sudo`** operations. This prevents using user paths which may be harmful

## USER Privilege Lines

The fourth line, which dictates the root user’s `sudo` privileges, is different from the preceding lines. Let’s take a look at what the different fields mean:

* <mark style="color:purple;">**`chris`**</mark> `ALL=(ALL:ALL) ALL`\
  The first field indicates the username that the rule will apply to (root)\

* `chris`<mark style="color:purple;">**`ALL`**</mark>`=(ALL:ALL) ALL`\
  The first “ALL” indicates that this rule applies to all hosts\

* `chris ALL=(`<mark style="color:purple;">**`ALL`**</mark>`:ALL) ALL`\
  This “ALL” indicates that the **root** user can run commands as all users\

* `chris ALL=(ALL:`<mark style="color:purple;">**`ALL`**</mark>`) ALL`\
  This “ALL” indicates that the **root** user can run commands as all groups\

* `chris ALL=(ALL:ALL)`` `<mark style="color:purple;">**`ALL`**</mark>\
  The last “ALL” indicates these rules apply to all commands.

This means that the`chris` user can run any command using **`sudo`**, as long as they provide their password.

###

## Group Privilege Lines

The next two lines are similar to the user privilege lines, but they specify **`sudo`** rules for **groups**. Names beginning with a **`%`** indicate group names.

In the screenshot, we see the **`admin`** group can execute any command as any user on any host. Similarly, the **`sudo`** group has the same privileges, but can execute as any group as well. Therefore, to have any user inherit these permissions, you can simply add users to this group. In this way, we can create **roles**.

##

## **Included /etc/sudoers.d Line**

The last line might look like a comment at first glance:

![Excerpt from the /etc/sudoers file regarding includes](<../../../../../../../.gitbook/assets/image (147).png>)

However, this line actually indicates that files within the **`/etc/sudoers.d`** directory will be sourced and applied as well.

{% hint style="info" %}
Files within that directory follow the same rules as the **`/etc/sudoers`** file itself. Any file that does not end in **`~`** and that does not have a **`.`** in it will be read and appended to the `sudo` configuration
{% endhint %}

This is mainly meant for applications to alter **`sudo`** privileges upon installation. Putting all of the associated rules within a single file in the **`/etc/sudoers.d`** directory can make it easy to see which privileges are associated with which accounts, and to reverse credentials easily without having to try to manipulate the **`/etc/sudoers`** file directly.
