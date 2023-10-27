# grep

I've mentioned this one already, but in case you missed it, have you ever heard of the `grep` command? It's short for **global regular expression print**, but don't let that long name scare you – it's super handy - I find myself using it all the time.

Basically, `grep` is like a searchlight for text. Give it a pattern, and it'll hunt through files to find matching lines and show them to you. And if you don't specify any files? No sweat! It'll just listen to whatever info is coming its way, like from another command's output.

##

## General Syntax

The syntax for the `grep` command is as follows:

```
grep [OPTIONS] PATTERN [FILE...]
```

The items in square brackets are optional.

* `OPTIONS` - Zero or more options. Grep includes a number of options that control its behaviour.
* `PATTERN` - Search pattern.
* `FILE` - Zero or more input file names.

{% hint style="info" %}
To be able to search the file, the user running the command must have read access to the file.
{% endhint %}

##

## Additional Options

### Search for a String in Files <a href="#search-for-a-string-in-files" id="search-for-a-string-in-files"></a>

The most basic usage of the `grep` command is to search for a string (text) in a file. For example, to display all the lines containing the string `bash` from the [`/etc/passwd`](https://linuxize.com/post/etc-passwd-file/) file, you would run the following command:

```
grep bash /etc/passwd
```

The output should look something like this:

```
root:x:0:0:root:/root:/bin/bash
example:x:1000:1000:linuxize:/home/linuxize:/bin/bash
```

If the string includes spaces, you need to enclose it in single or double quotation marks:

```
grep "Gnome Display Manager" /etc/passwd
```



### Using Grep to Filter the Output of a Command <a href="#using-grep-to-filter-the-output-of-a-command" id="using-grep-to-filter-the-output-of-a-command"></a>

A command’s output can be filtered with `grep` through piping, and only the lines matching a given pattern will be printed on the terminal.

For example, to find out which processes are running on your system as user `www-data` you can use the following [`ps`](https://linuxize.com/post/ps-command-in-linux/) command:

```
ps -ef | grep www-data
```

```
www-data 18247 12675  4 16:00 ?        00:00:00 php-fpm: pool www
root     18272 17714  0 16:00 pts/0    00:00:00 grep --color=auto --exclude-dir=.bzr --exclude-dir=CVS --exclude-dir=.git --exclude-dir=.hg --exclude-dir=.svn www-data
www-data 31147 12770  0 Oct22 ?        00:05:51 nginx: worker process
www-data 31148 12770  0 Oct22 ?        00:00:00 nginx: cache manager process
```

You can also chain multiple pipes in on command. As you can see in the output above there is also a line containing the `grep` process. If you don’t want that line to be shown pass the output to another `grep` instance as shown below.

```
ps -ef | grep www-data | grep -v grep
```

```
www-data 18247 12675  4 16:00 ?        00:00:00 php-fpm: pool www
www-data 31147 12770  0 Oct22 ?        00:05:51 nginx: worker process
www-data 31148 12770  0 Oct22 ?        00:00:00 nginx: cache manager process
```





### Invert Match (Exclude) <a href="#invert-match-exclude" id="invert-match-exclude"></a>

To display the lines that do not match a pattern, use the `-v` ( or `--invert-match`) option.

For example, to print the lines that do not contain the string `nologin` you would use:

```
grep -v nologin /etc/passwdCopy
```

```
root:x:0:0:root:/root:/bin/bash
colord:x:124:124::/var/lib/colord:/bin/false
git:x:994:994:git daemon user:/:/usr/bin/git-shell
linuxize:x:1000:1000:linuxize:/home/linuxize:/bin/bash
```



### Case Insensitive Search <a href="#case-insensitive-search" id="case-insensitive-search"></a>

By default, `grep` is **case sensitive**. This means that the uppercase and lowercase characters are treated as distinct.

To ignore case when searching, invoke `grep` with the `-i` option (or `--ignore-case`).

For example, when searching for `Zebra` without any option, the following command will not show any output i.e there are matching lines:

```
grep Zebra /usr/share/words
```

But if you perform a case insensitive search using the `-i` option, it will match both upper and lower case letters:

```
grep -i Zebra /usr/share/words
```

Specifying “Zebra” will match “zebra”, “ZEbrA” or any other combination of upper and lower case letters for that string.

```
zebra
zebra's
zebras
```



### Recursive Search <a href="#recursive-search" id="recursive-search"></a>

To recursively search for a pattern, invoke `grep` with the `-r` option (or `--recursive`). When this option is used `grep` will search through all files in the specified directory, skipping the symlinks that are encountered recursively.

To follow all symbolic links , instead of `-r`, use the `-R` option (or `--dereference-recursive`).

Here is an example showing how to search for the string `example.com` in all files inside the `/etc` directory:

```
grep -r example.com /etc
```

The output will include matching lines prefixed by the full path to the file:

```
/etc/hosts:127.0.0.1 node2.linuxize.com
/etc/nginx/sites-available/linuxize.com:    server_name example.com   www.example.com;
```

If you use the `-R` option, `grep` will follow all symbolic links:

```
grep -R example.com /etc
```

Notice the last line of the output below. That line is not printed when `grep` is invoked with `-r`because files inside the Nginx’s `sites-enabled` directory are symlinks to configuration files inside the `sites-available` directory.

```
/etc/hosts:127.0.0.1 node2.example.com
/etc/nginx/sites-available/example.com:    server_name example.com   www.example.com;
/etc/nginx/sites-enabled/example.com:    server_name example.com   www.example.com;
```



### Show Only the Filename <a href="#show-only-the-filename" id="show-only-the-filename"></a>

To suppress the default `grep` output, and print only the names of files containing the matched pattern, use the `-l` ( or `--files-with-matches`) option.

The command below searches through all files ending with `.conf` in the current working directory and prints only the names of the files containing the string `example.com`:

```
grep -l example.com *.conf
```

The output will look something like this:

```
tmux.conf
haproxy.conf
Copy
```

The `-l` option is usually used in combination with the recursive option `-R`:

```
grep -Rl example.com /tmp
```



### Search for Full Words <a href="#search-for-full-words" id="search-for-full-words"></a>

When searching for a string, `grep` will display all lines where the string is embedded in larger strings.

For example, if you search for “gnu”, all lines where “gnu” is embedded in larger words, such as “cygnus” or “magnum” will be matched:

```
grep gnu /usr/share/words
```

```
cygnus
gnu
interregnum
lgnu9d
lignum
magnum
magnuson
sphagnum
wingnut
```

To return only those lines where the specified string is a whole word (enclosed by non-word characters), use the `-w` ( or `--word-regexp`) option.Word characters include alphanumeric characters (`a-z`, `A-Z`, and `0-9`) and underscores (`_`). All other characters are considered as non-word characters.

If you run the same command as above, including the `-w` option, the `grep` command will return only those lines where `gnu` is included as a separate word.

```
grep -w gnu /usr/share/words
```

```
gnu
```



### Count Matches <a href="#count-matches" id="count-matches"></a>

To print a count of matching lines to standard output, use the `-c` ( or `--count`) option.

In the example below, we are counting the number of accounts that have `/usr/bin/zsh` as a shell.

```
grep -c '/usr/bin/zsh' /etc/passwd
```

```
4
```



### Search for Multiple Strings (Patterns) <a href="#search-for-multiple-strings-patterns" id="search-for-multiple-strings-patterns"></a>

Two or more search patterns can be joined using the OR operator `|`.

By default, `grep` interprets the pattern as a basic regular expression where the meta-characters such as `|` lose their special meaning, and their backslashed versions must be used.

In the example below we are searching all occurrences of the words `fatal`, `error`, and `critical` in the [Nginx log](https://linuxize.com/post/nginx-log-files/) error file:

```
grep 'fatal\|error\|critical' /var/log/nginx/error.log
```

If you use the extended regular expression option `-E`, then the operator `|` should not be escaped, as shown below:

```
grep -E 'fatal|error|critical' /var/log/nginx/error.log
```
