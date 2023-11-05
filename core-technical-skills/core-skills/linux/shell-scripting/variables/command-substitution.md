# Command Substitution

We can use command substitution so that a variable **contains the output of a command**, which would normally be output to the screen:

{% code title="Command Substitution" %}
```bash
user=$(whoami)
echo $user
Bob
```
{% endcode %}

This may look familiar to anyone who has been reading through this aide memoire - remember the section where we created [temporary user accounts](../../system-administration/account-administration/standard-user-accounts/#creating-temporary-user-accounts)? We were able to calculate 30 days in advance of the current date with command substitution.

You are only limited by your imagination - rather than list out tonnes of boring examples, have a play yourself and see what results you get within your variables
