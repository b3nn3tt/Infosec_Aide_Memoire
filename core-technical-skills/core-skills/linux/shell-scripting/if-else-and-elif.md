# if, else, and elif

We can write scripts that can perform certain actions depending on conditions using `if`, `else` and `elif`. The syntax for these things is quite particular so you need to be careful. At a high level, we are looking at...

{% code title="High Level Psuedo Code - if statement" %}
```
if [Some form of conditional test]
then
    do thing A
else
    do thing B
fi
```
{% endcode %}



## Simple if else Script

The easiest way to show this in action is to examine a working script with an `if` statement in it:

```bash
#!/bin/bash

echo "How old are you?"

read age

if [ $age -lt 18 ]
then
  echo "I think you are too young for this game"
else
  echo "Welcome to the club"
fi
```



## Simple if, elif, else Script

The above example only allows for 2 execution branches; one if a condition is true, or the other if not. This is fine if your script is fairly simple, however this can be rather limiting. So, we can add the `elif` statement to add further conditional checks, providing more granularity to the tool:

{% code title="High Level Psuedo Code - if else statement" %}
```bash
if [ <some test> ]
then
  <perform an action>
elif
then
  <perform this action instead>
else
  <perform yet another different action>
fi
```
{% endcode %}

Again, let's examine a working example:

```bash
#!/bin/bash

echo "How old are you?"

read age

if [ $age -lt 18 ]
then
  echo "I think you are too young for this game"
elif [ $age -gt 60 ]
then
  echo "Well, arent you the old codger"
else
  echo "Welcome to the club"
fi
```

{% hint style="info" %}
In both scripts, you are seeing operators such as `-lt` and `-gt`, which are short for **Less Than** and **Greater Than.** The table below contains a comprehensive list of operators you can use in your scripts
{% endhint %}



## Operators

| Operator                | Description                                   |
| ----------------------- | --------------------------------------------- |
| `!EXPRESSION`           | The EXPRESSION is false                       |
| `-n STRING`             | STRING length is greater than zero            |
| `-z STRING`             | The length of STRING is zero (empty)          |
| `STRING1 = STRING 2`    | STRING1 is equal to STRING2                   |
| `STRING1 != STRING 2`   | STRING1 is not equal to STRING2               |
| `INTEGER1 -eq INTEGER2` | INTEGER1 is equal to INTEGER2                 |
| `INTEGER1 -ne INTEGER2` | INTEGER1 is not equal to INTEGER2             |
| `INTEGER1 -gt INTEGER2` | INTEGER1 is greater then INTEGER2             |
| `INTEGER1 -lt INTEGER2` | INTEGER1 is less than INTEGER2                |
| `INTEGER1 -ge INTEGER2` | INTEGER1 is greater than or equal to INTEGER2 |
| `INTEGER1 -le INTEGER2` | INTEGER1 is less than or equal to INTEGER2    |
| `-d FILE`               | FILE exists and is a Directory                |
| `-e FILE`               | FILE exists                                   |
| `-r FILE`               | FILE exists and has read permission           |
| `-s FILE`               | FILE exists and is not empty                  |
| `-w FILE`               | FILE exists and has write permission          |
| `-x FILE`               | FILE exists and has execute permission        |
