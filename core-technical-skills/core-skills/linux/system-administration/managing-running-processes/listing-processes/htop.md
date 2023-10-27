# htop

An evolution over standard `top`, [htop](https://htop.dev/) provides an interactive, full terminal view process management environment. `htop` isn't always installed by default, however most distributions include it as an installable option their package manager repositories - _more on those later_. At the time of writing this section, `htop` had been adopted as part of the default installation for Ubuntu Server.

Running and interacting with `htop` is very simple:

```
htop
```

![A running instance of htop](<../../../../../../.gitbook/assets/image (75).png>)

`htop` has many additional options, and unlike top where those options are not apparent and require prior knowledge of shortcuts, `htop` trivialises the process through the use of function keys. They keys are fairly self explanatory, so take a quick look at the screenshot above to gain a quick familiarisation.

{% hint style="info" %}
Much like with top, if you want to be able to kill or renice any processes, you need to run `htop` as the `root` user. If you just want to display processes and possibly kill or change your own processes, you can do that as a regular user
{% endhint %}
