# Shell Variables

The shell has a clever way of holding onto bits of info that might come in handy during your session - they're stashed in things called variables. Here are a few examples to give you a taste:

* `$SHELL` - Identifies the shell you are using
* `$PS1` - Shapes the look of your shell prompt
* `$MAIL` - Points to your user's mailbox

Fancy a peek at all the variables your shell's holding onto? Just type in the `set` command. Oh, and a special group within these variables are the **environment variables**. These are shared with any new shells you pop open from the current one. To take a look at them, simply type `env`:

```
env
```

![Running env on a host](<../../../../../../.gitbook/assets/image (172).png>)

{% hint style="info" %}
You can type `echo $VALUE`, where **VALUE** is replaced by the name of a particular environment variable you want to list.&#x20;
{% endhint %}

Because there are **always** multiple ways to do anything in Linux, you can also type `declare` to get a list of the current environment variables and their values along with a list of shell functions.

Now, not all these variables are of your own making. The system itself sets a bunch, helping it remember things like where it's stashed configuration files, the whereabouts of mailboxes, or directories in your PATH. These variables can also hold onto little helpful nuggets, like how your shell prompts look, the length of your history list, or even the kind of operating system you're on.&#x20;

Fancy referencing the value of a variable? Pop a `$` before it, and drop it anywhere in a command line. Here's an example:

![This command prints the value of the USER variable, which holds your username](<../../../../../../.gitbook/assets/image (66).png>)

{% hint style="info" %}
`echo` is like saying "Hey, show this on the screen!"
{% endhint %}

When you kick off a shell session, be it by logging in through a virtual console or firing up a Terminal window, there's already a whole host of environment variables ready and waiting. The next section lays out a few of these variables - some come preset with a bash shell, while others are there for you to tweak as you fancy for various features.
