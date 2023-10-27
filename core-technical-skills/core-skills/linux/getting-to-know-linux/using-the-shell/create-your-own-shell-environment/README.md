# Create your Own Shell Environment

You can customise your shell for a more efficient workflow. By setting up aliases for frequently used commands and establishing environment variables for specific details, your tasks become streamlined. By including these configurations in your shell's setup files, they'll be at your fingertips every time you initiate a new shell session.

##

## Configure your Shell

Various configuration files dictate the behaviour of your shell. While some are applied universally for every user and shell session, others cater to individual users. The following table highlights the essential files for anyone utilising the bash shell in Linux:

| File              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| /etc/profile      | <p>This sets up user environment information for <strong>every user</strong>. It is executed when you first log in. This file provides values for your PATH, in addition to setting environment variables for such things as the location of your mailbox and the size of your history files. </p><p></p><p>Finally, <code>/etc/profile</code> gathers shell settings from configuration files in the <code>/etc/profile.d</code> directory.</p> |
| /etc/bashrc       | This executes for every user who runs the bash shell, each time a bash shell is opened. It sets the default prompt and may add one or more aliases. Values in this file can be **overridden** by information in each user’s `~/.bashrc` file.                                                                                                                                                                                                    |
| \~/.bash\_profile | <p>This is used by each individual user to enter information that is specific to his or her use of the shell. It is executed only once — when the user logs in. By default, it sets a few environment variables, and executes the user’s <code>~/.bashrc</code> file. </p><p></p><p><strong>This is a good place to add environment variables</strong> because, once set, they are inherited by future shells.</p>                               |
| \~/.bashrc        | This contains the information that is specific to each users bash shells. It is read when you log in and also each time you open a new bash shell. **This is the best location to add aliases** so that your shell picks them up.                                                                                                                                                                                                                |
| \~/.bash\_logout  | This executes each time you log out (exit the last bash shell).                                                                                                                                                                                                                                                                                                                                                                                  |

{% hint style="info" %}
Notice the use of `~` in the filenames to indicate that the file is located in the users home directory.
{% endhint %}

To modify the `/etc/profile` or `/etc/bashrc` files, you need root (superuser) privileges. However, rather than editing these files directly, it's advisable to set up an /`etc/profile.d/custom.sh` file for system-wide configurations.

Individual users have the freedom to alter the contents of the `$HOME/.bash_profile`, `$HOME/.bashrc`, and `$HOME/.bash_logout` files within their personal directories.

See the next section for some neat ideas on customisation.
