# usermod

One of the most common operations is to grant a new user account full `sudo` privileges. Whilst this can be achieved via `visudo`, you can achieve the same with `usermod` much easier. The caveat here is that a group must exist with the desired permissions you wish to grant. In this example, we will be adding a user to the `sudo` group, which is created by default on most modern systems.

{% hint style="info" %}
Debian-like operating systems, such as Ubuntu, create the `sudo` group with purpose similar to that of another group known as `wheel` . The `wheel` group is a special user group used on some Unix systems, mostly BSD systems, to control access to the `su` or `sudo` command.
{% endhint %}

To add a user to the sudo group, enter the following:

```
sudo usermod -aG sudo USERNAME
```

