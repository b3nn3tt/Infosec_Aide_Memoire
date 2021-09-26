# Sequential Commands

Sometimes, you may want a sequence of commands to run, with one command completing before the next command begins. You can do this by typing several commands on the same command line and separating them with semicolons \(;\):

```text
date ; troff -me verylargedocument | lpr ; date
```

In this example, I was formatting a huge document and wanted to know how long it would take. The first command `date` showed the date and time before the formatting started. The `troff` command formatted the document, and then piped the output to the printer. When the formatting was finished, the date and time were printed again, so I knew how long the troff command took to complete.

Another useful command to add to the end of a long command line is `mail`. You could add the following to the end of a command line:

```text
SOME COMMAND(S); mail -s "Finished the long command" chris@example.com
```

Then, for example, a mail message is sent to the user you choose after the command completes.

