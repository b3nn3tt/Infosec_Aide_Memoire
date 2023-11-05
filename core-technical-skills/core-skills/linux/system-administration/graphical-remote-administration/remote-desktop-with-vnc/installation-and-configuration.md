# Installation and Configuration

## Installing the Desktop Environment and VNC Server

Out of the box, an Ubuntu server doesn’t feature a graphical user interface or a VNC server. We’ll need to roll up our sleeves and set those up ourselves.

The beauty of Linux is the abundance of choices, and this holds true for selecting your VNC server and desktop environment. For our purposes, we’ll go with the latest version of the [xfce](https://xfce.org/) desktop environment coupled with the TightVNC server, both of which can be plucked straight from the official Ubuntu repositories. Renowned for their lightweight and efficient nature, xfce and TightVNC ensure a slick and responsive VNC experience, even when bandwidth is at a premium:

```bash
sudo apt update

sudo apt install xfce4 xfce4-goodies

sudo apt install tightvncserver
```

Next, run the **`vncserver`** command to set a VNC access password, create the initial configuration files, and start a VNC server instance:

```bash
vncserver
```

You’ll be prompted to enter and verify a password to access your machine remotely:

```bash
You will require a password to access your desktops.

Password:
Verify:
```

{% hint style="info" %}
The password must be between **six** and **eight** characters long. <mark style="color:red;">**Passwords more than 8 characters will be truncated automatically.**</mark>
{% endhint %}

After you've punched in your password and given it the nod, you'll come across the choice to set up a view-only password. Handy for those times you're in the spotlight, showing off your VNC server's capabilities without handing over the reins – folks can look but not touch. This step isn't a must, just a neat extra.

As you proceed, the setup will whisk together the default config files and provide details on how to connect. It'll also kick-start a VNC server instance on port **TCP 5901**, which VNC calls display **`:1`**. It's like having different channels on your TV – with **`:2`** channeling through **TCP 5902**, **`:3`** hopping onto **TCP 5903**, and so forth:

```
Would you like to enter a view-only password (y/n)? n
xauth:  file /home/sammy/.Xauthority does not exist

New 'X' desktop is your_hostname:1

Creating default startup script /home/sammy/.vnc/xstartup
Starting applications specified in /home/sammy/.vnc/xstartup
Log file is /home/sammy/.vnc/your_hostname:1.log
```

Note that if you ever want to change your password, or add a view-only password, you can do so with the `vncpasswd` command:

```bash
vncpasswd
```

At this point, the VNC server is installed and running. Now, let’s configure it to launch xfce and give us access to the server through a graphical interface.



## Configuring the VNC Server

The VNC server needs to know which commands to execute when it starts up. Specifically, VNC needs to know which graphical desktop environment it should connect to.

The commands that the VNC server runs at start-up are located in a configuration file called **`xstartup`** in the **`.vnc`** folder under your home directory. The start-up script was automatically generated when we ran the **`vncserver`** command in the previous step, but we'll create our own to launch the xfce desktop.

Because we are going to be changing how the VNC server is configured, first stop the VNC server instance that is running on port  with the following command:

```bash
vncserver -kill :1
```

Next, we will backup the original start-up script, and then edit the original:

```bash
mv ~/.vnc/xstartup ~/.vnc/xstartup.bak
nano ~/.vnc/xstartup
```

Add the following lines to the file:

{% code title="~/.vnc/xstartup" %}
```bash
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```
{% endcode %}

Save and close the file after adding these lines. If you used `nano`, do so by pressing **`CTRL`** + **`X`**, **`Y`**, then **`ENTER`**.

{% hint style="info" %}
The first command in the file, **`xrdb $HOME/.Xresources`**, tells VNC’s GUI framework to read the server user’s **`.Xresources`** file. **`.Xresources`** is where a user can make changes to certain settings of the graphical desktop, like terminal colours, cursor themes, and font rendering.



The second command tells the server to launch Xfce.



Whenever you start or restart the VNC server, these commands will execute automatically
{% endhint %}

To ensure that the VNC server will be able to use this new start-up file properly, you’ll need to make it executable, and then restart the VNC server:

```bash
chmod +x ~/.vnc/xstartup
vncserver -localhost
```

{% hint style="info" %}
Notice that this time the command includes the **`-localhost`** option, which binds the VNC server to your server’s loopback interface. This will cause VNC to only allow connections that originate from the server on which it’s installed. That probably sounds a bit weird on first pass, but stick with me here...



In the next step, we will establish an SSH tunnel between our local machine and the server, essentially tricking VNC into thinking that the connection from our local machine originated on the server. This strategy will add an extra layer of security around VNC, as the only users who will be able to access it are those that already have SSH access to your server.
{% endhint %}

With the configuration in place, you’re ready to connect to the VNC server from your local machine.



## Connecting to the VNC Desktop Securely

VNC, by default, isn't configured to communicate over encrypted channels. For a secure connection to your server, we'll set up an SSH tunnel, funneling our VNC client's traffic through it. This method wraps our VNC session in a layer of security.

To establish this secure conduit, initiate an SSH session from your local machine that's configured to forward to the VNC's localhost interface. You can do this from the terminal on Linux or macOS - and yes, even on modern Windows - using the following **`ssh`** command:

```bash
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

![A remote desktop session leveraging VNC over an SSH tunnel](<../../../../../../.gitbook/assets/image (105).png>)

When you are finished, press `Ctrl` + `c` in your local terminal to stop the SSH tunnel and return to your prompt. This will disconnect your VNC session as well.
