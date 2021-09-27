# Remove Password Requirement

Find the line belonging to the user or group you wish to remove the password requirement from, and add NOPASSWD in the following position:

```text
USER    ALL=(ALL:ALL) NOPASSWD:ALL
```

 `NOPASSWD` is a “tag” that means no password will be requested.

