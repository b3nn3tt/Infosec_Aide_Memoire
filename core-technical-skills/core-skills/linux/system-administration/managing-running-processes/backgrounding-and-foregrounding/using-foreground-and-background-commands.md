# Using Foreground and Background Commands

We will now work through an example of managing a task with a combination of backgrounding and foregrounding. A good illustration would be the creation and editing of a text file.

To begin with, we will open the nano editor:

```
nano example
```

![nano open, and basic text input](<../../../../../../.gitbook/assets/image (29).png>)

We will now send a signal to stop the nano process. This is known as `SIGTSTP`, and is issued by pressing `Ctrl` + `z`:

![The result of SIGTSTP](<../../../../../../.gitbook/assets/image (102).png>)

We can now see that the process is stopped, effectively in a frozen state, by running few commands we have previously seen, such as `ps`, `jobs` and `top`:

![Showing the stopped process with ps](<../../../../../../.gitbook/assets/image (26).png>)

![Showing the stopped process with htop](<../../../../../../.gitbook/assets/image (22).png>)

![Showing the stopped process with jobs](<../../../../../../.gitbook/assets/image (200).png>)

{% hint style="info" %}
When managing processes you have stopped, `jobs` provides the cleanest output. `ps` and `htop` require filtering most of the time, and aren't the most elegant choice in this scenario
{% endhint %}

At the moment, we have regained control of the terminal. We can therefore work on another task, and when we are ready, we can pick back up with our stopped process. To do this, we use the `fg` command, followed by the job number (depicted in `[ ]`), to re-focus our terminal on the stopped `nano` process:

```
fg 1
```

![The previously stopped process has been resumed](<../../../../../../.gitbook/assets/image (111).png>)

What if we want to perform a task that ordinarily would tie up our terminal, but also work on something else at the same time? To achieve this, we can run a task in the background. As we saw earlier, we can start a process in the background by appending an ampersand (`&`) to the command - that's all well and good, but what if we didn't have the foresight to start the process this way?&#x20;

We can background a running task, then set it to start back up again in the background with `bg`: In this example, we will run a command that ties up the terminal, and then press `Ctrl` + `z` to send `SIGTSTP`:

```
sudo tcpdump -i eth0 -ntvxw example.pcap
```

![Running process is stopped with SIGTSTP](<../../../../../../.gitbook/assets/image (64).png>)

Now, we can see by running jobs that the task has been stopped:

![Confirmation that the running process has stopped](<../../../../../../.gitbook/assets/image (160).png>)

Now, by entering `bg 1`, we can allow the process to continue in the background:

```
bg 1
```

![The process runs in the background, then it is foregrounded and terminated with Ctrl + c](<../../../../../../.gitbook/assets/image (142).png>)

{% hint style="info" %}
As you can see in the output, the terminal gets a little messy. Often, when you background a process, some of its output will still get printed to the terminal. This can be modified with STDOUT redirection of course, but things can still end up a little untidy - I have left this output in this state to illustrate the point
{% endhint %}
