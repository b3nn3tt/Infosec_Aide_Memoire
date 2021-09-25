# Command History

Being able to repeat a command you ran earlier in a shell session can be convenient. Recalling a long and complex command line that you mistyped can save you some trouble. Fortunately, some shell features enable you to recall previous command lines, edit those lines, or complete a partially typed command line.

The shell history is a list of the commands that you have entered before. Using the history command in a bash shell, you can view your previous commands. Then, using various shell features, you can recall individual command lines from that list and change them however you please.

The rest of this section describes how to do command-line editing, how to complete parts of command lines, and how to recall and work with the history list.

## **Customise History ENV Variables**

We can edit a number of environment variables to change how the history command operates and returns data, the most common including:

* **HISTCONTROL**
* **HISTIGNORE**
* **HISTTIMEFORMAT**

### **HISTCONTROL**

The **HISTCONTROL** variable defines whether or not to remove duplicate commands, commands that begin with spaces from the history, or both; **By default, both are removed** but you may find it more useful to only omit duplicates:

```text
export HISTCONTROL=ignoredups
```

### **HISTIGNORE**

The **HISTIGNORE** variable is particularly useful for filtering out basic commands that are run frequently, such as `ls`, `exit`, `history`, `bg`, etc:

```text
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

As you can see, the ls command is missing form history.

### **HISTTIMEFORMAT**

Lastly, **HISTTIMEFORMAT** controls date and/or time stamps in the output of the history command:

```text
history
1 2018-02-12 13:37:33 export HISTIGNORE="&:ls:[bf]g:exit:history"
2 2018-02-12 13:37:38 mkdir test
3 2018-02-12 13:37:40 cd test
4 2018-02-12 13:37:43 pwd
5 2018-02-12 13:37:51 export HISTTIMEFORMAT='%F %T '
```

In this example, we used `%F` \(Year-Month-Day ISO 8601 format\) and `%T` \(24-hour time\). Other formats can be found in the **strftime** man page_._

