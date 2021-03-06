# visudo

Primarily, the `visudo` command leverages an underlying text editor to edit, and check the integrity of the `/etc/visudo` file, which is the configuration file that governs the permissions and behaviours of the `sudo` command. If the user running `sudo` does not meet the authentication configuration in `/etc/sudoers`, they are denied permission to run a command with escalated privileges.

You should not edit `/etc/sudoers` directly by opening it in a text editor. Instead, edit it with `visudo`, which will verify its validity before saving the changes to disk. `visudo` edits the `/etc/sudoers` file in a safe fashion. It locks the `/etc/sudoers` file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors. If the `/etc/sudoers` file is currently being edited by someone else, or by you in another session, you will receive a message to try again later.

Depending on which distribution you are running, `visudo` will leverage one of several text editors. The most common editor is `vi`, although more and more distributions are using `nano` lately as it is much more user friendly, and changes to the file are relatively modest.

### visudo Command Options



| **Option** | Description |
| :--- | :--- |
| `-c` | Enable check-only mode. The existing `/etc/sudoers` file will be checked for syntax errors, owner and mode. A message will be printed to the standard output describing the status of `/etc/sudoers` unless the `-q` option was specified. If the check completes successfully, `visudo` will exit with a value of `0`. If an error is encountered, `visudo` will exit with a value of `1` |
| `-f sudoers` | Specify an alternate `/etc/sudoers` file location. With this option, `visudo` will edit \(or check\) the`sudoers` file of your choice, instead of the default, `/etc/sudoers`. The lock file used is the specified `sudoers` file with "`.tmp`" appended to it.   In check-only mode only, the argument to `-f` may be **-**, indicating that `sudoers` will be read from the standard input |
| `-h` | The `-h` \(help\) option causes `visudo` to print a short help message to the standard output and exit |
| `-q` | Enable quiet mode. In this mode details about syntax errors are not printed. This option is only useful when combined with the `-c` option |
| `-s` | Enable strict checking of the `sudoers` file. If an alias is used before it is defined, `visudo` will consider this a parse error. Note that it is not possible to differentiate between an alias and a hostname or username that consists solely of uppercase letters, digits, and the underscore \(**`_`**\) character |
| `-V` | The `-V` \(version\) option causes `visudo` to print its version number and exit |

