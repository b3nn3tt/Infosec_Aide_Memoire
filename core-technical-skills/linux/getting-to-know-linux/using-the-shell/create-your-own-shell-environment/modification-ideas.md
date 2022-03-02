# Modification Ideas

## Setting your Prompt

Your prompt consists of a set of characters that appear each time the shell is ready to accept a command. The `PS1` environment variable sets what the prompt contains, and is what you will interact with most of the time. If your shell requires additional input, it uses the values of PS2, PS3, and PS4.

When your Linux system is installed, often a prompt is set to contain more than just a dollar sign or pound sign. For example, in **Fedora** or **Red Hat Enterprise Linux**, your prompt is set to include the following information:

* Username
* Hostname
* Base-name of the working directory

That information is often surrounded by brackets and followed by a dollar sign (for regular users) or a pound sign (for the root user). The following is an example of that prompt:

![Example of a regular terminal prompt](<../../../../../.gitbook/assets/image (14).png>)

If you change directories, the base-name would change to the name of the new directory. Likewise, if you were to log in as a different user or to a different host, that information would change. You can use several special characters (indicated by adding a backslash to a variety of letters) to include different information in your prompt.

Special characters can be used to output your Terminal number, the date, and the time as well as other pieces of information. The bash man page provides some examples.

{% hint style="info" %}
If you are setting your prompt temporarily by typing at the shell, you should put the value of PS1 in quotes. For example, you could type:\
\
**`$ export PS1="[\t \w]\$ "`**\
\
to see a prompt that looks like this:\
\
**\[20:26:32 /var/spool]$.**

To make a change to your prompt permanent, add the value of `PS1` to your `.bashrc` file in your home directory (assuming that you are using the bash shell).
{% endhint %}

Refer to the Bash Prompt [HOWTO](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO) for information on changing colours, commands, and other features of your bash shell prompt.

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
