# Copying, Moving, and Removing Files

Commands for moving, copying, and deleting files are fairly straight forward:

* `cp` - Used to copy a file
* `mv` - Used to move \(or rename\) a file
* `rm` - Used to remove \(delete\) a file

These commands can be used to act on individual files and directories, or recursively to act on many files and directories at once.

## Copying Files

Here are some examples of using the `cp` command to copy files from one location to another:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Command</th>
      <th style="text-align:left">Result</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><code>cp abc def</code>
      </td>
      <td style="text-align:left">Copies <code>abc</code> to the new name <code>def</code> in the same directory</td>
    </tr>
    <tr>
      <td style="text-align:left"><code>cp abc ~</code>
      </td>
      <td style="text-align:left">Copies <code>abc</code> to your home directory (<code>~</code>), retaining
        the name <code>abc</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>cp -r /usr/share/doc/bash-completion* /tmp/a/</code>
      </td>
      <td style="text-align:left">
        <p>Copies the bash-completion directory, and <b>all of the files it contains</b>,
          to <code>/tmp/a/</code>
        </p>
        <p>&lt;code&gt;&lt;/code&gt;</p>
        <p>On copying, current date/time stamps are used, and permissions are determined
          by your <code>umask</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><code>cp -ra /usr/share/doc/bash-completion* /tmp/b/</code>
      </td>
      <td style="text-align:left">
        <p>Copies the bash-completion directory, and <b>all of the files it contains</b>,
          to <code>/tmp/b/</code>
        </p>
        <p>&lt;code&gt;&lt;/code&gt;</p>
        <p>Thanks to the archive (<code>-a</code>) option, the date/time stamps and
          permissions are unmodified by the copy, and retain the details of the original
          files</p>
      </td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
The `cp` command is typically aliased with the `-i` option in order to prevent you from inadvertently overwriting files. 
{% endhint %}

## Moving and Renaming Files

To move or rename a file, we leverage the `mv` command. When we "rename" a file in Linux, what we are really doing is moving the file to the same directory it currently sits in, and calling the newly moved file by a new name. This gives the illusion that the original file has simply been modified, when this is not technically accurate.

The following table has some examples of the `mv` command in action:

| Command | Result |
| :--- | :--- |
| `mv abc def` | Renames `abc` to the new name `def` in the same directory |
| `mv abc ~` | Moves `abc` to your home directory \(`~`\), retaining the name `abc` |
| mv /home/joe/mymemos/ /home/joe/Documents/ | Moves the`/home/joe/mymemos` directory \(and all its contents\) to the `/home/joe/Documents` directory |

{% hint style="info" %}
By default, the `mv` command overwrites any existing files if the file to which you are moving exists. However, many Linux systems alias the `mv` command so that it uses the `-i` option, which causes mv to prompt you before overwriting existing files. Here’s how to check if that is true on your system:

`$ alias mv`
{% endhint %}

## Removing Files

Here are some examples of the `rm` command:

| Command | Result |
| :--- | :--- |
| `rm abc` | Deletes the `abc` file |
| `rm *` | Removes all of the **files** in the current directory; doesn’t remove directories and/or any files that start with a dot |

If you want to remove a directory, you need to use the recursive \(`-r`\) option, or use the alternative command `rmdir` - not that the directory must be empty for this to work.

Consider the following examples:

| Command | Result |
| :--- | :--- |
| `rmdir /home/joe/nothing` | Only removes the directory \(nothing\) if it is **empty** |
| `rm -r /home/joe/bigdir` | Removes the directory `bigdir` and all of its contents \(files and multiple levels of subdirectories\), but it prompts you before each is removed |
| `rm -rf /home/joe/hugedir` | As before, but minus the prompts - make sure you are SURE! |

{% hint style="info" %}
As with the `cp` and `mv` commands, `rm` is also usually aliased to include the `-i` option. This can prevent the damage that can come from an inadvertent recursive remove \(`-r`\) option.
{% endhint %}

