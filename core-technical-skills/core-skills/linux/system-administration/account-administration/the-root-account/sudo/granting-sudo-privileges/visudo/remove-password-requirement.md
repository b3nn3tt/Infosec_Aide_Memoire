# Remove Password Requirement

Find the line belonging to the user or group you wish to remove the password requirement from, and add NOPASSWD in the following position:

```
USER    ALL=(ALL:ALL) NOPASSWD:ALL
```

&#x20;`NOPASSWD` is a “tag” that means no password will be requested.
