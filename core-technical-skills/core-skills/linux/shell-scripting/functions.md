# Functions

However





When it comes to scripts, functions are basically Inception; _a script within a script..._

![Hello Mr Charles...](<../../../../.gitbook/assets/image (211).png>)

Functions are useful when we need to execute the same code multiple times. Rather than re-writing the same chunk of code over and over, we just write it once as a function and then **call** that function as needed. Put another way, a function is a subroutine, or a code block that implements a set of operations – a “black box” that performs a specified task.

Functions may be written in two different formats. The first format is more common to Bash scripts:

{% code title="Function - typical bash syntax" %}
```bash
function function_name {
commands...
}
```
{% endcode %}

However, bash will happily accept another format, which is likely more familiar to people who have experience programming in C:

{% code title="Function - C-like syntax" %}
```bash
function_name () {
commands...
}
```
{% endcode %}

{% hint style="info" %}
For all intents and purposes, the formats are functionally identical and are a matter of personal preference. My recommendation is that you pick the once you prefer, or are most familiar with, and stick with it, but don't hop between the two...
{% endhint %}

So, let's look at a script where a function in created, and then called:

{% code title="Function Call Example" %}
```bash
#!/bin/bash

print_me () {
echo "You have been printed!"
}

print_me
```
{% endcode %}

![Example of a function call in a bash script](<../../../../.gitbook/assets/image (132).png>)

{% hint style="info" %}
Note that when a functioned is created, it will not execute unless it is explicitly called. Some script writers place all their functions at the very top of their scripts, and they are then called much further down as the need arises; This is where functions differ from the rest of the elements you will find in a typical script, which are executed sequentially from top to bottom.

However, a function **MUST** be placed in the script **BEFORE** it is called, or the call will fail.
{% endhint %}

Functions can also accept arguments, making them very versatile and therefore useful in our scripting:

{% code title="Function call with command argument" %}
```bash
#!/bin/bash

pass_arg () {
echo "Today's random number is: $1"
}

pass_arg $RANDOM
```
{% endcode %}

In this case, we passed a random number, `$RANDOM`, into the function, which outputs it as `$1`, the functions first argument. Note that the function definition (`pass_arg()`) contains parentheses. In other programming languages, such as C, these would contain the expected arguments, but in Bash the parentheses serve only as decoration. They are never used. Also note that the function definition (the function itself) must appear in the script before it is called. Logically, we can’t call something we have not defined.

In addition to passing arguments to Bash functions, we can of course return values from Bash functions as well. Bash functions do not actually allow you to return an arbitrary value in the traditional sense. Instead, a Bash function can return an exit status (zero for success, non-zero for failure) or some other arbitrary value that we can later access from the `$?` global variable. Alternatively, we can set a global variable inside the function or use command substitution to simulate a traditional return.





