# Shell Scripting

Lots of people are put off at the idea of scripting or programming as it can look quite complicated, and yes, some scripts appear rather unwieldy at first glance (this can be for many reasons, not least of which is poor commenting by the author). But when you boil things down to basics, scripts are really simple things.

Try to think of script like a recipe - you put in the ingredients, and after a few practice runs trying to not burn the house down, you have a delicious meal to show for all your efforts. All a script really is, is a list of commands performed one after the other. You can leverage pretty much any commands you like, and by learning a few key functions you will find in this section, you can add some quite powerful logic to your script - before you know it, you will automating things without consciously thinking about it.

When you try to execute a shell script in Linux, the terminal you are running in (and therefore, the shell itself) will try to execute it natively by default. However, as part of that execution, the script will look for the presence of what is known as a **defined required interpreter**. This is set on the first line of the script using what is known as the **shebang** (haSH BANG), depicted as follows:

```bash
#!/bin/bash
```

As you can see, this is an **ABSOLUTE PATH** to the location of the desired interpreter in the Linux File System (LFS). 99 out of 100, BASH can be found in /bin, so this is a standard way to start a script. After you have defined the required interpreter, simply add the commands you want and the script executes them in order, much like any program. We can leverage things like variables, user input, if/else/elif statements, loops, functions and so on in order to get jobs done.

{% hint style="info" %}
Recently, various Linux distributions made the leap from BASH to ZSH, meaning that a lot of scripts broke overnight
{% endhint %}

We can "comment out" lines in our scripts with a hash character, which instructs the system to not interpret (execute) that line - this is how we leave comments in our code to remind ourselves, or inform others, what our scripts are doing:

```bash
#!/bin/bash

#The following line prints a message to the terminal
echo "Hello World"
```

{% hint style="info" %}
Scripts must be executable in order to use them. So, double check those permissions
{% endhint %}
