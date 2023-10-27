# Modification Ideas

## Setting your Prompt

Your shell prompt, which is a series of characters displayed each time the shell awaits a command, is governed by the PS1 environment variable. While PS1 is the main prompt you'll engage with, the shell turns to PS2, PS3, and PS4 when it seeks further input. Upon installing Linux, the prompt usually displays more than a mere dollar or pound sign.

In distributions like [Fedora](https://fedoraproject.org/) or [Red Hat Enterprise Linux](https://www.redhat.com/en/technologies/linux-platforms/enterprise-linux), the prompt typically includes:

* Username
* Hostname
* Base-name of the working directory

This information is commonly bracketed and capped with a dollar sign for a standard user, or a hash for root (superuser). An example of such a prompt would be:

![Example of a regular terminal prompt](<../../../../../../.gitbook/assets/image (124).png>)

When you navigate to a different directory, the base-name in your prompt updates to reflect that new location. Similarly, if you sign in as another user or onto a different server, the displayed information adjusts accordingly.

To personalise your prompt further, you can employ various special characters. By prefixing certain letters with a backslash, you can display details like your Terminal number, the current date, or the time, among other things. For a detailed list of these characters and their functions, you can consult the bash man page.

{% hint style="info" %}
When adjusting your prompt for a brief period directly within the shell, remember to enclose the PS1 value in quotes. For instance, entering:\


&#x20;    `$ export PS1="[\t \w]$ "`



will produce a prompt resembling:

\
&#x20;    `[20:26:32 /var/www]$`

\
To ensure your prompt alteration lasts, incorporate the PS1 value into the .bashrc file located in your home directory, assuming you're operating within the bash shell.
{% endhint %}

Refer to the Bash Prompt [HOWTO](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO) for information on changing colours, commands, and other features of your bash shell prompt.

##

## **Adding Environment Variables**

You might want to consider adding a few environment variables to your `.bashrc` file. These can help make working with the shell more efficient and effective:

* **TMOUT**\
  This sets how long the shell can be inactive before bash automatically exits. _**The value is the number of seconds for which the shell has not received input**_. This can be a nice security feature, in case you leave your desk while you are still logged in to Linux. \
  \
  To prevent being logged off while you are working, you may want to set the value to something like `TMOUT=1800` (to allow **30 minutes** of idle time). You can use any Terminal session to close the current shell after a set number of seconds, for example, `TMOUT=30`.
* **PATH**\
  As described earlier, the PATH variable sets the directories that are searched for the commands that you use. If you often use directories of commands that are not in your path, you can permanently add them. To do this, add a PATH variable to your `.bashrc` file. For example, to add a directory called `/getstuff/bin`, add the following:\
  \
  `PATH=$PATH:/getstuff/bin ; export PATH` \
  \
  This example first reads all of the current path directories into the new PATH($PATH), adds the `/getstuff/bin` directory, and then exports the new PATH. \
  \
  **See the subnote for a word of caution when working with PATH...**
* **WHATEVER**\
  You can create your own environment variables to provide shortcuts in your work. Choose any name that is not being used and assign a useful value to it. For example, if you do lots of work with files in the `/work/time/files/info/memos` directory, you could set the following variable:\
  \
  `M=/work/time/files/info/memos ; export M`\
  \
  You could make that your current directory by typing `cd $M`. You could run a program from that directory called hotdog by typing `$M/hotdog`. You could edit a file from there called bun by typing vi `$M/bun`.
