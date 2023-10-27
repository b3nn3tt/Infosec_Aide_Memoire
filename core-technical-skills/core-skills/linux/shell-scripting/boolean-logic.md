# BOOLEAN Logic

Boolean logical operators like `AND` (`&&`), and `OR` (`||`) are somewhat mysterious because Bash uses them in a variety of ways. Putting it as simply as is possible, BOOLEAN logic looks for a **True** or **False** scenario, and depending on which operator you use, a certain action will be performed. So, with `AND`, some initial condition is tested and if it is found to be True, it will then perform the second - BOTH elements have to be found True for successful execution. With `OR`, the same conditional test will take place, but either one or the other side must be found True, not both. The examples below demonstrate this, and they are fairly simple, so once you've seen them things become quite clear.

A common use is in command lists, which are chains of commands whose flow is controlled by operators:

{% code title="BOOLEAN operator example - AND" %}
```bash
user2=ubuntu
grep $user2 /etc/passwd && echo "$user2 found!"
```
{% endcode %}

![Example of BOOLEAN AND](<../../../../.gitbook/assets/image (213).png>)

So, what happened here then? A variable was declared, holding the value of a valid user name. Then, the `grep` command  was used to search the `/etc/passwd` file for an entry that matched the username; in this case, `ubuntu`. So, the `grep` command completes, and there is indeed a match, there was a matching user accounts with the name `ubuntu`, meaning that the BOOLEAN True/False test was positive.

In this situation, the AND result must be true for the next command to be executed, else execution will cease. On this occasion execution continues, and the second command (`echo`) is executed, printing our message to the terminal (**`STDOUT`**).

If we change the value of user2 to a user not present in the system, and run the same BOOLEAN command, you will notice that the output is different:

![BOOLEAN AND with a false outcome](<../../../../.gitbook/assets/image (183).png>)

On this occasion, the AND condition fails as the username `doesnotexist` cannot be found in the `/etc/passwd` file, hence the second command is never executed.

If we were to modify the command, replacing `AND` with `OR`, we would see our desired echo message, despite the username not appearing in the `/etc/passwd` file:

![BOOLEAN OR with successful execution from a FALSE conditon](<../../../../.gitbook/assets/image (171).png>)

As you have doubtlessly worked out, this is because with the `OR` statement, either condition needs to be True, not both, and because the second condition is merely an `echo` command, it was always going to be true irrespective of the initial conditional check.

{% hint style="info" %}
Whilst the above examples are very simple, the power of BOOLEAN operators means that your scripts can contain some quite powerful decision making calls, depending on certain conditions being made
{% endhint %}
