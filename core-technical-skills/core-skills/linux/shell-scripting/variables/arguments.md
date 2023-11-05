# Arguments

Arguments, as well as being things I often get into at home about the jobs I forgot to do... are the things we pass to a command or script upon execution:

```bash
ls -l /opt
```

{% hint style="info" %}
In the above command, there is one option (`-l`) and one argument, (`/opt`)
{% endhint %}

You can prescribe for arguments in your script using special variables:

* `$0` - The name of the script being executed
* `$1` - The FIRST command line argument passed
* `$2` - The SECOND command line argument passed

So, let's look at an example script:

{% code title="Example Script to handle Arguments: example.sh" %}
```bash
#!/bin/bash

echo "Welcome to the $0 script."
echo "The first two arguments are $1 and $2"
```
{% endcode %}

So, if we pass the following command with arguments:

```bash
./example.sh apples pears
Welcome to the ./example.sh script.
The first two arguments are apples and pears
```

There are other special arguments we can use:

| Argument    | Description                                      |
| ----------- | ------------------------------------------------ |
| `$0`        | The name of the Bash script                      |
| `$1 - $9`   | The first 9 arguments to the Bash script         |
| `$#`        | Number of arguments passed to the Bash script    |
| `$@`        | All arguments passed to the Bash script          |
| `$?`        | The exit status of the most recently run process |
| `$$`        | The process ID of the current script             |
| `$USER`     | The username of the user running the script      |
| `$HOSTNAME` | The hostname of the machine                      |
| `$RANDOM`   | A random number                                  |
| `$LINENO`   | The current line number in the script            |
