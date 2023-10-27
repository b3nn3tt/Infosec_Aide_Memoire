# Command Substitution

We can use command substitution so that a variable contains the output of a command, which would normally be output to the screen:

{% code title="Command Substitution" %}
```bash
user=$(whoami)
echo $user
Bob
```
{% endcode %}

