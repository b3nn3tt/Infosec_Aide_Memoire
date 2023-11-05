# Lock Down Rules

There are a number of ways that you can achieve more control over how `sudo` reacts to a call. The `updatedb` command associated with the `mlocate` package is relatively harmless on a single-user system. If we want to allow users to execute it with root privileges without having to type a password, we can make a rule like this:

```
. . .
GROUPONE      ALL = NOPASSWD: /usr/bin/updatedb
. . .
```

`NOPASSWD` is a “tag” that means no password will be requested. It has a companion command called `PASSWD`, which is the default behaviour. A tag is relevant for the rest of the rule unless overruled by its “twin” tag later down the line.

For instance, we can have a line like this:

```
. . .
GROUPTWO      ALL = NOPASSWD: /usr/bin/updatedb, PASSWD: /bin/kill
. . .
```

This would mean that any member of `GROUPTWO` can execute `updatedb` without being prompted for a password, however the use of `kill` would still prompt a password request.



Another helpful tag is `NOEXEC`, which can be used to prevent some dangerous behaviour in certain programs. For example, some programs, like `less`, can spawn other commands by typing this from within their interface:

```
!command_to_run
```

This basically executes any command the user gives it with the same permissions that `less` is running under, which can be quite dangerous. To restrict this, we could use a line like this:

```
. . .
username      ALL = NOEXEC: /usr/bin/less
. . .
```
