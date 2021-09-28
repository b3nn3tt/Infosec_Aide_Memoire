# Using Foreground and Background Commands

We will now work through an example of managing a task with a combination of backgrounding and foregrounding. A good illustration would be the creation and editing of a text file.

To begin with, we will open the nano editor:

```text
nano example
```

![nano open, and basic text input](../../../../../.gitbook/assets/image%20%2841%29.png)

We will now send a signal to stop the nano process. This is known as `SIGTSTP`, and is issued by pressing `Ctrl` + `z`:

![The result of SIGTSTP](../../../../../.gitbook/assets/image%20%2850%29.png)

We can now see that the process is stopped, effectively in a frozen state, by running few commands we have previously seen, such as `ps`, `jobs` and `top`:

![Showing the stopped process with ps](../../../../../.gitbook/assets/image%20%2864%29.png)

![Showing the stopped process with htop](../../../../../.gitbook/assets/image%20%2837%29.png)

![Showing the stopped process with jobs](../../../../../.gitbook/assets/image%20%2868%29.png)

{% hint style="info" %}
When managing processes you have stopped, `jobs` provides the cleanest output. `ps` and `htop` require filtering most of the time, and aren't the most elegant choice in this scenario
{% endhint %}



