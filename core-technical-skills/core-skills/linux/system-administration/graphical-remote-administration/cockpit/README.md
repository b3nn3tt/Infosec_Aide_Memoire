# Cockpit

Cockpit is the best browser-based Linux system administration tool that I have seen. It provides a unified interface for a multitude of administrative tasks. It harnesses various Linux APIs through the cockpit-bridge, but as an administrator, the key takeaway is the consistency and stability Cockpit offers for system management.

Initiating Cockpit is a breeze – simply activate the cockpit service, and then navigate to the Cockpit interface using a web browser. Its modular nature means it's constantly evolving; you can integrate new plugins to enhance your management console, which we'll discuss in more detail later.

After installation, to access the interface remotely, direct your web browser to TCP port 9090 on the server, using either the hostname or IP address. By default, Cockpit secures this port using HTTPS, but you have the option to switch to HTTP if necessary."

{% hint style="info" %}
If you've retained the self-signed certificate generated during the initial setup of Cockpit, your browser will likely flag up a security warning upon connection. This is standard practice for self-signed certificates.&#x20;



To proceed, you'll need to bypass the warning. Depending on which web browser you're using, this typically involves clicking on 'Advanced' and then accepting the risk or adding an exception, thereby granting you access to the Cockpit interface.
{% endhint %}

You will then be presented with a login screen. Here, you can enter your username and password as you would if you were logging in locally or via SSH. Use the **root** user, or a user with **`sudo`** privileges if you want to change your system configuration. A regular user can see, but cannot change most settings:

![Cockpit login screen for a RHEL server](<../../../../../../.gitbook/assets/image (150).png>)

![A view of the Cockpit interface once authenticated](<../../../../../../.gitbook/assets/image (181).png>)

The default Cockpit dashboard comes packed with a robust suite of features, with an extensive array of additional functionalities available for integration, especially on RHEL and Fedora systems. It presents you with real-time system metrics, including CPU, memory and swap usage, as well as disk I/O and network activity.&#x20;

The left-hand navigation pane is your gateway to a wealth of system management tasks — from perusing logs, managing storage and network configurations, to handling user and group accounts, services, and more.
