# Command Line Recall

Once you punch in a command, it gets saved in your shell's history list. This list persists in your current shell session until you call it quits. After you exit, the list gets saved to a history file, ready for a rerun in your next session.&#x20;

If you dig up an old command in a subsequent shell session, you can always give it a tweak in the same fashion we saw earlier.

##

## The history Command

To view your history list, use the **history** command. Enter the command without any additional options, or optionally followed by a number, to list that many of the most recent commands. For example:

```
history 8
382 date 
383 ls /usr/bin | sort -a | more 
384 man sort 
385 cd /usr/local/bin 
386 man more 
387 useradd -m /home/chris -u 101 chris 
388 passwd chris 
389 history 8
```

As you can see from the output, a number precedes each command line in the list. You can recall one of those commands using an exclamation point (!), followed by the number that correlates against your desired command:

```
!382
```

Alternatively, to simply repeat the most recent command, you can enter the following:

```
!!
```

Keep in mind that when an exclamation point is used, the command runs blind without presenting an opportunity to confirm the command you’re referencing...
