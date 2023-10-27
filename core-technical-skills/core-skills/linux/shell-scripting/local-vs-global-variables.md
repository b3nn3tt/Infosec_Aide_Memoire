# Local Vs Global Variables

Now that we have a basic understanding of variables and functions, we can dig deeper and discuss **variable scope**. The scope of a variable is simply the context in which it has meaning. By default, a variable has a global scope, meaning it can be accessed throughout the entire script.

In contrast, a local variable can only be seen within the function, block of code, or subshell in which it is defined. We can “overlay” a global variable, giving it a local context, by preceding the declaration with the local keyword, leaving the global variable untouched. The general syntax for a local variable is:

```bash
local name="Joe"
```

Let's take a look at an example script:

{% code title="Variable scope script" %}
```bash
#!/bin/bash

name1="John"
name2="Jason"

name_change() {
  local name1="Edward"
  echo "Inside of this function, name1 is $name1 and name2 is $name2"
  name2="Lucas"
}

echo "Before the function call, name1 is $name1 and name2 is $name2"

name_change

echo "After the function call, name1 is $name1 and name2 is $name2"
```
{% endcode %}

Let's break this script down, and then we will take a look at it in action. First note that we declared two global variables, setting `name1` to `John` and `name2` to `Jason`. Then, we defined a function, and inside that function we declared a local variable called `name1`, setting the value to `Edward`. Since this was a local variable, the previous global assignment was not affected; `name1` will still be set to `John` outside this function.

Next, we set `name2` to `Lucas`, and since we did not use the local keyword, we are changing the global variable, and the assignment sticks both inside and outside of the function. Based on this example, the following two points summarize variable scope:

* Changing the value of a local variable with the same name as a global one will **not** affect its global value\

* Changing the value of a global variable inside of a function – without having declared a local variable with the same name – **will** affect its global value

So, let's see the script run and the end result:

![Local and Global variable scopes](<../../../../.gitbook/assets/image (19).png>)
