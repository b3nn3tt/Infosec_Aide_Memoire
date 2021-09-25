# Create your Own Shell Environment

You can tune your shell to help you work more efficiently. You can set aliases to create shortcuts to your favourite command lines, and environment variables to store bits of information. By adding those settings to shell configuration files, you can have the settings available every time you open a shell.

## Configure your Shell

Several configuration files support how your shell behaves. Some of the files are executed for every user and every shell, whereas others are specific to the user who creates the configuration file. The table below shows the files that are of interest to anyone using the bash shell in Linux:

<table>
  <thead>
    <tr>
      <th style="text-align:left">File</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">/etc/profile</td>
      <td style="text-align:left">
        <p>This sets up user environment information for <b>every user</b>. It is
          executed when you first log in. This file provides values for your PATH,
          in addition to setting environment variables for such things as the location
          of your mailbox and the size of your history files.</p>
        <p></p>
        <p>Finally, <code>/etc/profile</code> gathers shell settings from configuration
          files in the <code>/etc/profile.d</code> directory.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">/etc/bashrc</td>
      <td style="text-align:left">This executes for every user who runs the bash shell, each time a bash
        shell is opened. It sets the default prompt and may add one or more aliases.
        Values in this file can be <b>overridden </b>by information in each user&#x2019;s <code>~/.bashrc</code> file.</td>
    </tr>
    <tr>
      <td style="text-align:left">~/.bash_profile</td>
      <td style="text-align:left">
        <p>This is used by each individual user to enter information that is specific
          to his or her use of the shell. It is executed only once &#x2014; when
          the user logs in. By default, it sets a few environment variables, and
          executes the user&#x2019;s <code>~/.bashrc</code> file.</p>
        <p></p>
        <p><b>This is a good place to add environment variables</b> because, once
          set, they are inherited by future shells.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">~/.bashrc</td>
      <td style="text-align:left">This contains the information that is specific to each users bash shells.
        It is read when you log in and also each time you open a new bash shell. <b>This is the best location to add aliases</b> so
        that your shell picks them up.</td>
    </tr>
    <tr>
      <td style="text-align:left">~/.bash_logout</td>
      <td style="text-align:left">This executes each time you log out (exit the last bash shell).</td>
    </tr>
  </tbody>
</table>

{% hint style="info" %}
Notice the use of `~` in the filenames to indicate that the file is located in the users home directory.
{% endhint %}

To change the /etc/profile or /etc/bashrc files, you must be the root user. It is better to create an /etc/profile.d/custom.sh file to add system-wide settings instead of editing those files directly, however. Users can change the information in the $HOME/.bash\_profile, $HOME/.bashrc, and $HOME/.bash\_logout files in their own home directories.

Enter the following to edit and add stuff to your $HOME/.bashrc file:

