# Running VNC as a System Service

By setting up the VNC server to run as a systemd service, you can start, stop, and restart it as needed, like any other service. You can also use systemd’s management commands to ensure that VNC starts when your server boots up.

First, create a new unit file called `/etc/systemd/system/vncserver@.service`:

```
sudo nano /etc/systemd/system/vncserver@.service
```

The `@` symbol at the end of the name will let us pass in an argument you can use in the service configuration. You’ll use this to specify the VNC display port you want to use when you manage the service.

Add the following lines to the file. Be sure to change the value of `User`, `Group`, `WorkingDirectory`, and the username in the value of `PIDFILE` to match your username:

{% code title="/etc/systemd/system/vncserver@.service" %}
```
[Unit]
Description=Start TightVNC server at startup
After=syslog.target network.target

[Service]
Type=forking
User=USERNAME
Group=GROUPNAME
WorkingDirectory=/home/USERNAME

PIDFile=/home/USERNAME/.vnc/%H:%i.pid
ExecStartPre=-/usr/bin/vncserver -kill :%i > /dev/null 2>&1
ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 -localhost :%i
ExecStop=/usr/bin/vncserver -kill :%i

[Install]
WantedBy=multi-user.target
```
{% endcode %}

{% hint style="info" %}
&#x20;The `ExecStartPre` command stops VNC if it’s already running. The `ExecStart` command starts VNC and sets the color depth to 24-bit color with a resolution of 1280x800. You can modify these start-up options as well to meet your needs. Also, note that the `ExecStart` command again includes the `-localhost` option.
{% endhint %}

Save and close the file. Then, make the system aware of the new unit file:

```
sudo systemctl daemon-reload
sudo systemctl enable vncserver@1.service
```

{% hint style="info" %}
The `1` following the `@` sign signifies which display number the service should appear over, in this case the default `:1` as was discussed in the Installation and Configuration phase
{% endhint %}

Stop the current instance of the VNC server if it’s still running, then start it as you would start any other systemd service:

```
vncserver -kill :1
sudo systemctl start vncserver@1
```

You can verify that it started with this command:

```
sudo systemctl status vncserver@1
```

If it started correctly, the output should look like this:

{% code title="Output" %}
```
● vncserver@1.service - Start TightVNC server at startup
     Loaded: loaded (/etc/systemd/system/vncserver@.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-05-07 17:23:50 UTC; 6s ago
    Process: 39768 ExecStartPre=/usr/bin/vncserver -kill :1 > /dev/null 2>&1 (code=exited, status=2)
    Process: 39772 ExecStart=/usr/bin/vncserver -depth 24 -geometry 1280x800 :1 (code=exited, status=0/SUCCESS)
   Main PID: 39795 (Xtightvnc)
...
```
{% endcode %}

&#x20;Your VNC server is now ready to use whenever your server boots up, and you can manage it with [`systemctl` commands](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) like any other systemd service.

