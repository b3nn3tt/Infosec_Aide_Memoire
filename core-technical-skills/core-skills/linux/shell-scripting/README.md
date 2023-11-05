---
description: Automate all the things!
---

# Shell Scripting

Alright, let’s talk about the elephant in the room – scripting and programming.

I know, just a glance at a page full of code can make some people want to hurl themselves off something tall. It can seem like an ancient cryptic language, and even the pros sometimes scratch their heads at a particularly gnarly piece of code.&#x20;

But here’s the secret: if you strip away all the jargon and complex-looking parts, <mark style="color:green;">**scripts are pretty straightforward!**</mark>

Try to think of script like a recipe - you put in the ingredients, and after a few practice runs trying to not burn the house down, you have a delicious meal to show for all your efforts. All a script really is, is a list of commands performed one after the other. You can leverage pretty much any commands you like, and by learning a few key functions you will find in this section, you can add some quite powerful logic to your script - before you know it, you will automating things without consciously thinking about it.



## The Principles of Scripting

It's a common misconception among beginners that there is only one "correct" way to write a script. The truth is, scripting is far more flexible than it initially appears. While it's beneficial to follow best practices for efficiency and maintainability, I encourage all aspiring scripters to remember these two key principles:

1. If it looks stupid but it works, it's **NOT** stupid
2. If you find yourself performing a task more than once, automate it. Work <mark style="color:green;">**SMART**</mark> not <mark style="color:red;">**HARD**</mark>

In your early stages, focus more on making things work - you have all the time in the world to refine a functional script, but if you go for style over substance at the outset, you'll never leave the starting blocks.&#x20;

The second principle is important to wrap your head around. Scripting is, at its core, an efficiency and convenience mechanism. The idea is simple - automate, or make consistently repeatable, processes to make your life easier. Nowhere does it say that those processes have to be complex. So, if you find yourself constantly looking through log files for a certain event, then write a small script that achieves that, set it to run as a cron job, and spend your time doing other things! Remember, SMART not HARD



## Script Execution

In Linux, when you initiate the execution of a shell script, the terminal, by default, attempts to process it using the shell environment it's running in. The script, upon execution, searches for a specific line that indicates the required interpreter for the script. This line, commonly known as the shebang (a contraction of "hash bang"), is typically the first line in the script and is written as follows:

```bash
#!/bin/bash
```

As you can see, this is an **absolute path** to the location of the desired interpreter in the filesystem. 99 times out of 100, **`bash`** can be found in **`/bin`**, so this is a standard way to start a script. After you have defined the required interpreter, simply add the commands you want and the script executes them in order, much like any program. We can leverage things like variables, user input, if/else/elif statements, loops, functions and so on in order to get jobs done.

We can "comment out" lines in our scripts with a hash character, which instructs the system to not interpret, or execute that line - this is how we leave comments in our code to remind ourselves, or inform others, what our scripts are doing:

```bash
#!/bin/bash

#The following line prints a message to the terminal
echo "Hello World"
```

{% hint style="info" %}
Scripts must be executable in order to use them. So, double check those permissions. If you need a reminder, then you can always review the  [File Permissions](../getting-to-know-linux/moving-around-the-filesystem/file-permissions-and-ownership/modifying-permissions-with-chmod.md) section
{% endhint %}
