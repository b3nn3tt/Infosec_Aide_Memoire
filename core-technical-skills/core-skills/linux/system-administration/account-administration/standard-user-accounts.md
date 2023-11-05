# Standard User Accounts

As we now know, Linux is a multi-user operating system, which means it is designed to support multiple users on the same system. Each user has a separate account with a unique username and password. These accounts are typically known as "standard user accounts" and provide users with the ability to access their own files, run applications, and perform basic tasks.

Unlike administrative accounts, standard user accounts have limited access rights to the system's files and settings. This ensures that users cannot unintentionally (or intentionally) make system-wide changes that could affect other users or the stability of the system itself.



## Administration of Standard User Accounts

The administration of standard user accounts is a critical task for system administrators. It involves creating, managing, and sometimes revoking user access.



### Creating User Accounts

When you’re setting up a new account for someone, you’ll want to use the **`useradd`** command. It’s a bit like handing out a new set of keys to the castle, except it’s just to their own little quarters. Here’s how you might go about it:

```
useradd -m -s /bin/bash newuser
passwd newuser
```

This pair of commands sets up a new user called **`newuser`**, gives them a home directory (**`-m`**), and sets their default shell to bash (**`-s /bin/bash`**). Straight after, we set a password for them with the **`passwd`** command.

{% hint style="info" %}
If you don't set a password for a new user account on Linux, by default, the account is created without a password, but the user won't be able to log in through the usual login prompts.



Most Linux distributions require a password for login, <mark style="color:red;">**so if there's no password set, the system effectively locks the account**</mark>. To make the account usable, you would generally either set a password, as above, or set up some form of password-less authentication, such as SSH key authentication.
{% endhint %}

To adopt security best practices, it's vital that users create their own passwords. Initially, we set a provisional password to get the account up and running. However, we must rectify this by ensuring the user is prompted to change their password at the first login. This can be accomplished with the command:

```
passwd --expire newuser
```

This action ensures our new user is required to select a new, private password upon first accessing the system, thereby reinforcing the security of the account.



### Creating Temporary User Accounts

Occasionally, you might need to set up a temporary account, perhaps for a contractor or a guest speaker at your company. Think of it as giving them a day pass to your system. Here's the lowdown on how to do it:

```
useradd -m -s /bin/bash -e $(date -d "+30 days" +%F) tempuser
passwd --expire tempuser
```

As before, we levereage useradd to create the new user, only this time we add some additional options:

* **`-e`**: specifies that the account will expire, and uses the result of the following section to determine when
* **`$(date -d "+30 days" +%F)`**: calculates the date 30 days from now and formats it in a way the **`useradd`** command understands

This time,  we don't even bother setting a temporary password - we immediately "expire" the account so on first logon, the temp user sets their own password. This is far more efficient.

{% hint style="info" %}
When an account locks out this way, it isn't deleted - all user files will remain in place unless removed by a suitably privileged administrator.
{% endhint %}

#### Extending the Expiry Date

There may come a time when you need to extend the expiry date for a temporary user account. This might be necessary due to project extensions, continued need for access, or other operational reasons. To do this, we'll use the **`usermod`** command as follows:

```
sudo usermod -e YYYY-MM-DD username
```

or

```
sudo usermod -e $(date -d "+30 days" +%F) username

```

In the first command, the **`-e`** option is followed by a specific expiry date in **`YYYY-MM-DD`** format. This is useful when you know the exact date the account should expire. If you’re looking to extend the expiry by a certain number of days rather than to a fixed date, the second command will be your method of choice. It increments the expiry date by 30 days from the current date.

#### Remove an Expiry Date

Sometimes, you'll want to remove the expiry date from an account altogether. This could happen if a temporary position becomes permanent, or if an expired account needs to be reinstated. To remove an expiry date, the **`usermod`** command is again our tool:

```
sudo usermod -e '' username
```

By setting the expiry date to an empty string **`''`** with the **`-e`** option, we're instructing the system that the account should no longer have an expiry date. This will reactivate a previously expired account, or ensure that an active account remains so indefinitely.

Both methods are straightforward and can be executed with ease, giving you the flexibility to manage account expirations effectively.



### Locking User Account

Sometimes, you might find yourself needing to put a user account on ice, denying access for a user. This could be for any number of reasons: perhaps the person is going on an extended leave, there might be some security concerns, or it's simply part of a routine check-up on who has access to your systems.

Locking an account is akin to putting a padlock on someone's front door. It's 100% reversible, so you're not throwing away the key, but while it's locked, they won't be able to log in or access system resources.

Here’s how you can lock a user account:

```
usermod -L username
```

The **`-L`** flag with the **`usermod`** command is the digital equivalent of clapping a padlock on the account of **`username`**. This command doesn't alter with the user's password, but it does slap a "Do Not Enter" sign on their account that the login system respects.

If you're wondering about subsequently unlocking it, because maybe the user returns from their sabbatical or the security concerns have been cleared up, you just use the `-U` flag:

```
usermod -U username
```

Voila, the padlock comes off, and it's like it was never there. The user can come back, log in, and carry on as if nothing happened.

{% hint style="info" %}
Locking accounts is a good practice in situations such as:

* **Employee Leave**\
  When someone is on maternity leave or a sabbatical, you want to ensure their account isn't accessible, just as a security precaution.
* **Contractors or Temporary Workers**\
  Once the job is done, you might lock their account until it's confirmed there's no further need for their access.
* **Security Concerns**\
  If you suspect an account has been compromised, you'll lock it immediately to prevent any unauthorised access.
* **Account Disputes**\
  If there's a dispute about who should have access to an account, locking it can be a neutral action while things are being sorted.
* **Pending Investigations**\
  If there's any ongoing investigation that requires an account to remain untouched, locking it can ensure the integrity of the data until the investigation is complete.



Remember, when you lock an account, it's a good policy to inform the user (if appropriate) and document the reason and the date of the action for future reference. Security and transparency go hand in hand, after all.
{% endhint %}



### Delete a User Account









