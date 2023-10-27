# Granting sudo privileges

So, now we know what `sudo` is, it's time to configure some privileges. We can do this several ways, but by far the most common is to add a user to the already existent `sudo` group. We can achieve this with the `usermod` command. Alternatively, we can edit the `/etc/sudoers` file with `visudo`. In this section, we will explore both methods.

Let's get started.
