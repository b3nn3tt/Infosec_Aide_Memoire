# Useful sudo Hints

There are a few more pieces of information that may be useful when dealing with `sudo`.

### Run As

If you specified a user or group to “run as” in the configuration file (`/etc/sudoers`), you can execute commands as those users by using the `-u` and `-g` flags, respectively:

```
sudo -u specified_user command #run command as the provided user

sudo -g specified_group command #run command as the provided group
```

### sudo Timer

For convenience, by default, `sudo` will save your authentication details for a certain amount of time in one terminal. This means you won’t have to type your password in again until that timer runs out. For security purposes, if you wish to clear this timer when you are done running administrative commands, you can run:

```
sudo -k
```

If, on the other hand, you want to “prime” the `sudo` command so that you won’t be prompted later, or to renew your `sudo` lease, you can always type:

```
sudo -v
```

You will be prompted for your password, which will be cached for later `sudo` uses until the `sudo` time frame expires.

### Privilege Enumeration

If you are simply wondering what kind of privileges are defined for your username, you can type:

```
sudo -l
```

This will list all of the rules in the `/etc/sudoers` file that apply to your user. This gives you a good idea of what you will or will not be allowed to do with `sudo` as the current user.

### User Insults

For some fun, you can add the following line to your `/etc/sudoers` file with `visudo`:

```
. . .
Defaults   insults
. . .
```

This will cause `sudo` to return an insult when a user types in an incorrect password. See the following example:

![](<../../../../../../../.gitbook/assets/image (186).png>)

