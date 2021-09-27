# Installation and Configuration

## Installing the Desktop Environment and VNC Server

By default, an Ubuntu server does not come with a graphical desktop environment or a VNC server installed, so you’ll begin by installing those.

There are many options when it comes to which VNC server, and indeed which desktop environment you would like. Here, we will install packages for the latest [xfce](https://xfce.org/) desktop environment, and the TightVNC package available from the official Ubuntu repository. Both xfce and TightVNC are known for being lightweight and fast, which will help ensure that the VNC connection will be smooth and stable even on slower connections.

{% code title="Installing necessary software" %}
```text
sudo apt update

sudo apt install xfce4 xfce4-goodies

sudo apt install tightvncserver
```
{% endcode %}

Next, run the `vncserver` command to set a VNC access password, create the initial configuration files, and start a VNC server instance:

```text
vncserver
```



You’ll be prompted to enter and verify a password to access your machine remotely:

{% code title="Output" %}
```text
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
```text
Would you like to enter a view-only password (y/n)? n
xauth:  file /home/sammy/.Xauthority does not exist

New 'X' desktop is your_hostname:1

Creating default startup script /home/sammy/.vnc/xstartup
Starting applications specified in /home/sammy/.vnc/xstartup
Log file is /home/sammy/.vnc/your_hostname:1.log
```
{% endcode %}

 Note that if you ever want to change your password, or add a view-only password, you can do so with the `vncpasswd` command:

```text
vncpasswd
```

At this point, the VNC server is installed and running. Now, let’s configure it to launch xfce and give us access to the server through a graphical interface.



## Configuring the VNC Server

The VNC server needs to know which commands to execute when it starts up. Specifically, VNC needs to know which graphical desktop environment it should connect to.

The commands that the VNC server runs at start-up are located in a configuration file called `xstartup` in the `.vnc` folder under your home directory. The start-up script was automatically generated when we ran the `vncserver` command in the previous step, but we'll create our own to launch the xfce desktop.

Because we are going to be changing how the VNC server is configured, first stop the VNC server instance that is running on port **`TCP 5901`** with the following command:

```text
vncserver -kill :1
```

Next, we will backup the original start-up script, and then edit the original:

```text
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
nano ~/.vnc/xstartup
```

Add the following lines to the file:

{% code title="~/.vnc/xstartup" %}
```text
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```
{% endcode %}













