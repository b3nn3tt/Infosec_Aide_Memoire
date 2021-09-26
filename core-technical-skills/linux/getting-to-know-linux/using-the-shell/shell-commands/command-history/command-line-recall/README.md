# Command Line Recall

After you type a command, the entire command line is saved in your shell’s history list. The list is stored in the current shell until you exit the shell. After that, it is written to a history file, from which any command can be recalled to be run again in your next session.

After a command is recalled, you can modify the command line, as described earlier.

## The history Command

To view your history list, use the **history** command. Enter the command without options, or optionally followed by a number, to list that many of the most recent commands. For example:

```text
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

As you can see from the output, a number precedes each command line in the list. You can recall one of those commands using an exclamation point \(!\), followed by the number that correlates against your desired command:

```text
!382
```

Alternatively, to simply repeat the most recent command, you can enter the following:

```text
!!
```

Keep in mind that when an exclamation point is used, the command runs blind without presenting an opportunity to confirm the command you’re referencing...

