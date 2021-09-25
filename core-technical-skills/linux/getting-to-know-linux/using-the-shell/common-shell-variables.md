# Common Shell Variables

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">BASH</td>
      <td style="text-align:left">This contains the full pathname of the bash command. This is usually <code>/bin/bash</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BASH_VERSION</td>
      <td style="text-align:left">This is a number representing the current version of the bash command.</td>
    </tr>
    <tr>
      <td style="text-align:left">EUID</td>
      <td style="text-align:left">This is the effective user ID number of the current user. It is assigned
        when the shell starts, based on the user&#x2019;s entry in the <code>/etc/passwd</code> file</td>
    </tr>
    <tr>
      <td style="text-align:left">FCEDIT</td>
      <td style="text-align:left">If set, this variable indicates the text editor used by the fc command
        to edit history commands. If this variable isn&#x2019;t set, the vi command
        is used</td>
    </tr>
    <tr>
      <td style="text-align:left">HISTFILE</td>
      <td style="text-align:left">This is the location of your history file. It is typically located at
        $HOME/. bash_history</td>
    </tr>
    <tr>
      <td style="text-align:left">HISTFILESIZE</td>
      <td style="text-align:left">This is the number of history entries that can be stored. After this number
        is reached, the oldest commands are discarded. The default value is 1000</td>
    </tr>
    <tr>
      <td style="text-align:left">HISTCMD</td>
      <td style="text-align:left">This returns the number of the current command in the history list</td>
    </tr>
    <tr>
      <td style="text-align:left">HOME</td>
      <td style="text-align:left">This is your home directory. It is your current working directory each
        time you log in or type the cd command with any options</td>
    </tr>
    <tr>
      <td style="text-align:left">HOSTTYPE</td>
      <td style="text-align:left">This is a value that describes the computer architecture on which the
        Linux system is running. For Intel-compatible PCs, the value is i386, i486,
        i586, i686, or something like i386-linux. For AMD 64-bit machines, the
        value is x86_64</td>
    </tr>
    <tr>
      <td style="text-align:left">MAIL</td>
      <td style="text-align:left">This is the location of your mailbox file. The file is typically your
        username in the <code>/var/spool/</code>mail directory</td>
    </tr>
    <tr>
      <td style="text-align:left">OLDPWD</td>
      <td style="text-align:left">This is the directory that was the working directory before you changed
        to the current working directory</td>
    </tr>
    <tr>
      <td style="text-align:left">OS TYPE</td>
      <td style="text-align:left">This name identifies the current operating system. For Fedora Linux, the <code>OSTYPE</code> value
        is either linux or linux-gnu, depending on the type of shell you are using.
        (Bash can run on other operating systems as well)</td>
    </tr>
    <tr>
      <td style="text-align:left">PATH</td>
      <td style="text-align:left">
        <p>This is the colon-separated list of directories used to find commands
          that you type. The default value for regular users varies for different
          distributions but typically includes the following:</p>
        <p></p>
        <p><code>/bin:/usr/bin:/ usr/local/bin:/usr/bin/X11:/usr/X11R6/bin:~/bin</code> 
        </p>
        <p></p>
        <p>You need to type the full path or a relative path to a command that you
          want to run which is not in your PATH. For the root user, the value also
          includes:</p>
        <p></p>
        <p><code>/sbin</code>, <code>/usr/sbin</code>, and <code>/usr/local/sbin</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">PPID</td>
      <td style="text-align:left">This is the process ID of the command that started the current shell (for
        example, the Terminal window containing the shell)</td>
    </tr>
    <tr>
      <td style="text-align:left">PROMPT_COMMAND</td>
      <td style="text-align:left">This can be set to a command name that is run each time before your shell
        prompt is displayed. Setting PROMPT_COMMAND=date lists the current date/time
        before the prompt appears</td>
    </tr>
    <tr>
      <td style="text-align:left">PS1</td>
      <td style="text-align:left">This sets the value of your shell prompt. There are many items that you
        can read into your prompt (date, time, username, hostname, and so on).
        Sometimes a command requires additional prompts, which you can set with
        the variables PS2, PS3, and so on</td>
    </tr>
    <tr>
      <td style="text-align:left">PWD</td>
      <td style="text-align:left">This is the directory that is assigned as your current directory. This
        value changes each time you change directories using the cd command</td>
    </tr>
    <tr>
      <td style="text-align:left">RANDOM</td>
      <td style="text-align:left">Accessing this variable causes a random number to be generated. The number
        is between 0 and 99999</td>
    </tr>
    <tr>
      <td style="text-align:left">SECONDS</td>
      <td style="text-align:left">This is the number of seconds since the time the shell was started</td>
    </tr>
    <tr>
      <td style="text-align:left">SHLVL</td>
      <td style="text-align:left">This is the number of shell levels associated with the current shell session.
        When you log in to the shell, the SHLVL is 1. Each time you start a new
        bash command (by, for example, using su to become a new user, or by simply
        typing bash), this number is incremented</td>
    </tr>
    <tr>
      <td style="text-align:left">TMOUT</td>
      <td style="text-align:left">This can be set to a number representing the number of seconds the shell
        can be idle without receiving input. After the number of seconds is reached,
        the shell exits. This security feature makes it less likely for unattended
        shells to be accessed by unauthorized people. (This must be set in the
        login shell for it actually to cause the shell to log out the user)</td>
    </tr>
  </tbody>
</table>

