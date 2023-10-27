# Starting a Background Process

If you have programs that you want to run while you continue to work in the shell, you can place the programs in the background. To place a program in the background at the time you run the program, type an ampersand (`&`) at the end of the command line, like this:

```
find /home/ubuntu/ -name example.txt > search_results.txt &
```

![Running find in the background](<../../../../../../.gitbook/assets/image (39).png>)

The ampersand (`&`) runs that command line in the background. Notice that the job number, \[1], and process ID number, 16398, are displayed when the command is launched. To check which commands you have running in the background, use the jobs command, as shown.

{% hint style="info" %}
In this example, the `find` command completes very quickly, so when we run `jobs` it shows as complete. However, other commands that take much longer, or have no natural end point without manual termination, will show a different status, such as `Running`
{% endhint %}
