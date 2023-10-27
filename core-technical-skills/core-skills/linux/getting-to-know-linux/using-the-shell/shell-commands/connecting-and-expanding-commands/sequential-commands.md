# Sequential Commands

In situations where you wish to execute multiple commands sequentially, ensuring that each finishes before the next starts, you can string them together in a single line using semicolons (`;`) as separators:

```
date ; troff -me verylargedocument | lpr ; date
```

In this example, I was formatting a huge document and wanted to know how long it would take. The first command `date` showed the date and time before the formatting started. The `troff` command formatted the document, and then piped the output to the printer. When the formatting was finished, the date and time were printed again, so I knew how long the `troff` command took to complete.

Another useful command to add to the end of a long command line is `mail`. You could add the following to the end of a command line:

```
SOME COMMAND(S); mail -s "Finished the long command" chris@example.com
```

Then, for example, a mail message is sent to the user you choose after the command completes.

{% hint style="info" %}
To use the `mail` command effectively, you typically need a mail server or Mail Transfer Agent (**MTA**) set up on your system or network.

The `mail` command is a simple Mail User Agent (MUA) that sends and receives mail using an underlying MTA like Sendmail, Postfix, or Exim. When you send an email using the `mail` command, it hands off the email to the MTA, which then takes care of delivering it to the intended recipient.

If you try to use the `mail` command without an MTA configured, the email will not be sent, or might get queued without delivery.
{% endhint %}
