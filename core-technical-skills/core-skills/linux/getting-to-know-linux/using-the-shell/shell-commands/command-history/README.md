# Command History

Ever had that moment where you think, "_I swear I just typed that exact command five minutes ago_"? Well, the shell's got your back.

If you've ever knocked up a super long command or just want a quick redo of something you've done, the shell has some nice tricks up its sleeve. Enter the shell history – it's like your diary, logging all those commands you've entered. Want to see? Just throw in the `history` command if you're using bash. From there, you've got the power to pull up those old commands, tweak them, or just run them again.&#x20;

Stick aroundfor the next bit, where we'll dive into the magic of command-line editing; finishing off half-typed command lines, and navigating through your command history.



## **Customise History ENV Variables**

The way the `history` command operates is steered by three environment variables:

* **HISTCONTROL**
* **HISTIGNORE**
* **HISTTIMEFORMAT**

###

### **HISTCONTROL**

The **HISTCONTROL** variable defines whether or not to remove any duplicate commands from your history, or commands that begin with spaces, or both!&#x20;

**By default, both are removed**

You may find it more useful to only omit duplicates:

```
export HISTCONTROL=ignoredups
```

###

### **HISTIGNORE**

The **HISTIGNORE** variable is particularly useful for filtering out basic commands that are run frequently, such as `ls`, `exit`, `history`, `bg`, etc:

```
export HISTIGNORE="&:ls:[bf]g:exit:history"

mkdir test

cd test

~/test# ls

~/test# pwd
/home/kali/test

~/test# ls

~/test# history
1 export HISTIGNORE="&:ls:[bf]g:exit:history"
2 mkdir test
3 cd test
4 pwd
```

As you can see, the `ls` command is missing form history.



### **HISTTIMEFORMAT**

Lastly, **HISTTIMEFORMAT** controls date and/or time stamps in the output of the history command:

```
history
1 2018-02-12 13:37:33 export HISTIGNORE="&:ls:[bf]g:exit:history"
2 2018-02-12 13:37:38 mkdir test
3 2018-02-12 13:37:40 cd test
4 2018-02-12 13:37:43 pwd
5 2018-02-12 13:37:51 export HISTTIMEFORMAT='%F %T '
```

In this example, we used `%F` (Year-Month-Day ISO 8601 format) and `%T` (24-hour time). Other formats can be found in the **strftime** man page_._
