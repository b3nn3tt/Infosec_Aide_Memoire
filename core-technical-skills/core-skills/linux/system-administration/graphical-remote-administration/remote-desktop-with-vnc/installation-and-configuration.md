# Installation and Configuration

## Installing the Desktop Environment and VNC Server

By default, an Ubuntu server does not come with a graphical desktop environment or a VNC server installed, so you’ll begin by installing those.

There are many options when it comes to which VNC server, and indeed which desktop environment you would like. Here, we will install packages for the latest [xfce](https://xfce.org/) desktop environment, and the TightVNC package available from the official Ubuntu repository. Both xfce and TightVNC are known for being lightweight and fast, which will help ensure that the VNC connection will be smooth and stable even on slower connections.

{% code title="Installing necessary software" %}
```
sudo apt update

sudo apt install xfce4 xfce4-goodies

sudo apt install tightvncserver
```
{% endcode %}

Next, run the `vncserver` command to set a VNC access password, create the initial configuration files, and start a VNC server instance:

```
vncserver
```



You’ll be prompted to enter and verify a password to access your machine remotely:

{% code title="Output" %}
```
You will require a password to access your desktops.

Password:
Verify:
```
{% endcode %}

{% hint style="info" %}
The password must be between six and eight characters long. Passwords more than 8 characters will be truncated automatically
{% endhint %}

Once you verify the password, you’ll have the option to create a view-only password. Users who log in with the view-only password will not be able to control the VNC instance with their mouse or keyboard. This is a helpful option if you want to demonstrate something to other people using your VNC server, but this isn’t required.

The process then creates the necessary default configuration files and connection information for the server. Additionally, it launches a default server instance on port **`TCP 5901`**. This port is called a _display port_, and is referred to by VNC as `:1`. VNC can launch multiple instances on other display ports, with `:2` referring to port **`TCP 5902`**, `:3` referring to **`TCP 5903`**, and so on:

{% code title="Output" %}
```
Would you like to enter a view-only password (y/n)? n
xauth:  file /home/sammy/.Xauthority does not exist

New 'X' desktop is your_hostname:1

Creating default startup script /home/sammy/.vnc/xstartup
Starting applications specified in /home/sammy/.vnc/xstartup
Log file is /home/sammy/.vnc/your_hostname:1.log
```
{% endcode %}

&#x20;Note that if you ever want to change your password, or add a view-only password, you can do so with the `vncpasswd` command:

```
vncpasswd
```

At this point, the VNC server is installed and running. Now, let’s configure it to launch xfce and give us access to the server through a graphical interface.



## Configuring the VNC Server

The VNC server needs to know which commands to execute when it starts up. Specifically, VNC needs to know which graphical desktop environment it should connect to.

The commands that the VNC server runs at start-up are located in a configuration file called `xstartup` in the `.vnc` folder under your home directory. The start-up script was automatically generated when we ran the `vncserver` command in the previous step, but we'll create our own to launch the xfce desktop.

Because we are going to be changing how the VNC server is configured, first stop the VNC server instance that is running on port **`TCP 5901`** with the following command:

```
vncserver -kill :1
```

Next, we will backup the original start-up script, and then edit the original:

```
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
nano ~/.vnc/xstartup
```

Add the following lines to the file:

{% code title="~/.vnc/xstartup" %}
```
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```
{% endcode %}

Save and close the file after adding these lines. If you used `nano`, do so by pressing `CTRL` + `X`, `Y`, then `ENTER`.

{% hint style="info" %}
The first command in the file, `xrdb $HOME/.Xresources`, tells VNC’s GUI framework to read the server user’s `.Xresources` file. `.Xresources` is where a user can make changes to certain settings of the graphical desktop, like terminal colours, cursor themes, and font rendering.

The second command tells the server to launch Xfce.&#x20;

Whenever you start or restart the VNC server, these commands will execute automatically
{% endhint %}

To ensure that the VNC server will be able to use this new start-up file properly, you’ll need to make it executable, and then restart the VNC server:

```
chmod +x ~/.vnc/xstartup
vncserver -localhost
```

{% hint style="info" %}
Notice that this time the command includes the `-localhost` option, which binds the VNC server to your server’s loopback interface. This will cause VNC to only allow connections that originate from the server on which it’s installed.&#x20;

This is because in the next step we will establish an SSH tunnel between our local machine and the server, essentially tricking VNC into thinking that the connection from our local machine originated on the server. This strategy will add an extra layer of security around VNC, as the only users who will be able to access it are those that already have SSH access to your server.
{% endhint %}

With the configuration in place, you’re ready to connect to the VNC server from your local machine.



## Connecting to the VNC Desktop Securely

VNC itself doesn’t use secure protocols when connecting. To securely connect to your server, we will establish an SSH tunnel, and then tell our VNC client to connect using that tunnel rather than making a direct connection. In this way, we achieve a secure connection.

To achieve this, create an SSH connection on your local computer that securely forwards to the `localhost` connection for VNC. We can do this via the terminal on Linux (or macOS, and even Windows these days) with the following `ssh` command:

```
ssh -L 59000:localhost:5901 -C -N -l USERNAME VNC_SERVER_IP
```

Here’s what this `ssh` command’s options mean:

* `-L 59000:localhost:5901`: The `-L` switch specifies that the specified port on our local computer, **`TCP 59000`** is to be forwarded to the given host and port on the destination server **`localhost:5901`** meaning port **`TCP 5901`** on the destination server, defined as `VNC_SERVER_IP`. Note that the local port you specify is somewhat arbitrary; as long as the port isn’t already bound to another service, you can use it as the forwarding port for your tunnel\

* `-C`: This flag enables compression which can help minimize resource consumption and speed things up\

* `-N`: This option tells `ssh` that you don’t want to execute any remote commands. This setting is useful when you just want to forward ports\

* `-l USERNAME VNC_SERVER_IP`: The `-l` switch let’s you specify the user you want to log in as once you connect to the server. Make sure to replace `USERNAME` and `VNC_SERVER_IP` with the name of your **non-root user** and your server’s IP address

{% hint style="info" %}
This command establishes an SSH tunnel that forwards information from port `5901` on your VNC server to port `59000` on your local machine via port `22` on each machine, the default port for SSH.

This is more secure than simply opening up your server’s firewall to allow connections to port `5901`, as that would allow anyone to access your server over VNC. By connecting over an SSH tunnel, you’re limiting VNC access to machines that already have SSH access to the server.
{% endhint %}

Once the tunnel is running, use a VNC client to connect to `localhost:59000`. You’ll be prompted to authenticate using the password you set earlier. Once you are connected, you’ll see the default xfce desktop. It should look something like this:

![](<../../../../../../.gitbook/assets/image (105).png>)

When you are finished, press `Ctrl` + `c` in your local terminal to stop the SSH tunnel and return to your prompt. This will disconnect your VNC session as well.
