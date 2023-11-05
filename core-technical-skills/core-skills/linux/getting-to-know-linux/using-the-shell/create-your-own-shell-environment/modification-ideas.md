# Modification Ideas

## The Prompt

That little nudge your shell gives you, waiting for your next command - that's the **prompt**, and it's all down to an environment variable named **PS1**. While PS1 is the main prompt you'll engage with, it will  hand over to it's mates PS2, PS3, and PS4 for any extra bits and bobs the shell needs from you when things get a bit more complicated.

Now, when you first get started with Linux, your prompt is more than just a simple dollar or pound sign - it's got a bit more character. If you're working within the likes of Fedora or Red Hat Enterprise Linux, your prompt usually flashes your username, the name of your machine (or **hostname**), and the base name of the directory you're working in. It's like having the satnav display your exact location in the filesystem – pretty handy for knowing where you are and who you are at a glance.

This information is commonly bracketed and capped with a **dollar sign** for a standard user, or a **hash** for root (superuser). An example of such a prompt would be:

![Example of a regular terminal prompt](<../../../../../../.gitbook/assets/image (124).png>)

When you navigate to a different directory, the base-name in your prompt updates to reflect your new location. Likewise, if you sign in as another user, or remote onto a different server, the displayed information adjusts accordingly.



## Sprucing Up your Prompt

Now, if you're itching to give your prompt a bit more pizzazz, you've got a whole box of special characters to play with. Slap a backslash in front of certain letters, and you can have your prompt flashing things like your terminal number, today's date, or the current time! This might sound like small potatoes, but it can be really useful.

Fancy diving into the deep end? The man page for bash is a treasure trove – it's got the full lowdown on these special characters and how to make them strut their stuff in your prompt.

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
