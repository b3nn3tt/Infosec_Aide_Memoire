# while Loops

while loops are also fairly common, and execute code while an expression (or condition) is true. while loops have a simple format and, like `if` statements, use the square brackets (`[]`) to define the conditional test

From a high-level perspective, this is what we're looking at:

{% code title="Psuedo code - while loop" %}
```bash
while [ <some conditional test> ]
do
    <perform some action>
done
```
{% endcode %}

The easiest way to understand the difference between the types of loops is to write a script that performs the same job. So, we will create the same outcome as our for loop, and examine the difference:

```bash
#!/bin/bash

counter=1

while [ $counter -le 10 ]
do
  echo "192.168.1.$counter"
  ((counter++))
done
```

Aside from the obvious difference that this is no longer a "one-liner", we can see immediately that there is no defined list. Instead, a variable is declared with a fixed value (`counter=1`), and the condition states that this loop will run **while** the value of counter is **less that or equal to 10**.&#x20;

At the latter stages of the script, we see `counter++` - this simply means take the current value or `counter`, and add it to itself, which in our case means add 1, as per the original declaration. So, with each loop, counter goes up in value by 1, until it reaches 10 and the loop ends:

![Example of a while loop](<../../../../../.gitbook/assets/image (4).png>)

As you can see, although there is a clear difference in the logic being used, the outcome remains the same.
