# for Loops

for loops are very practical, and work very well in Bash "one-liners"; mini scripts that are really just long commands designed to be executed directly at the terminal. This type of loop is used to perform a given set of commands for each item defined in a list.

From a high-level, this is what we're looking at:

{% code title="Psuedo code example - for loop" %}
```bash
for variable-name in <list>
do
    <action to perform>
done
```
{% endcode %}

So, we will define a variable name, and that variable name will be used to represent each item in a defined list. The action we define will iterate over the list, replacing the placeholder we put in with the variable contents. With each pass, the variable content will be changed to the next item in the list, and this loop will continue until all items in the list have been run - or to put it another way, the loop will run FOR each item in the list.

Confused? Don't be, its a lot easier than it sounds. Take a look at the following example, which will be written as a "one-liner":

```bash
for ip in $(seq 1 10); do echo 192.168.1.$ip; done
```

So, let's quickly break this down:

1. We have defined a variable called `ip`, and we have also used the `seq` command with command substitution. All `seq` does in this case is count upwards from the first number to the last, so the loop will start with `ip` holding the value of `1`, then `2`, and so on all the way up to `10`. Simply put, `seq` creates our list of values, which will like this:\
   \
   1\
   2\
   3\
   4\
   5\
   6\
   7\
   8\
   9\
   10\

2. The command is split then by a `;`, which is a special character in Bash - it means "_first complete the command to the left, THEN move on to the next bit_". In this case, Bash will `echo` the IP address `192.168.1.$ip` , where `$ip` contains the value of our `ip` variable for this run of the loop. So on the first run, echo will print `192.168.1.1`, then `192.168.1.2`, and so on...\

3. The end of the "one-liner" contains another `;`, after which we see `done`. This signifies the end of the loop. So, the process will double back to the start, and continue to do so, until the final IP address with a value of .10, as per the `seq` value at the start of the command

So, when we run this for loop "one-liner", we get the following outcome:

![Simple for loop example](<../../../../../.gitbook/assets/image (170).png>)

{% hint style="info" %}
I can hear you thinking "Where does this have practical application?". There are lots of useful ways to leverage a for loop, but they are very powerful when you need to perform the same action on a number of different files.&#x20;

For example, I have a script that contains a list of applications I like to put on all my fresh system installations. Rather than manually install them all one by one, I wrote a for loop that takes the names of those applications as a list, and performs the same installation commands, swapping out the name of the application each time. By the time my kettle has boiled and my tea is made, my applications are all installed.
{% endhint %}
