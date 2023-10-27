# Cockpit

Cockpit is the best browser-based Linux system administration tool that I have seen. It brings together a range of Linux administrative activities into one interface and taps into a diverse set of Linux APIs using cockpit-bridge. As someone doing Linux administration, however, you just need to know that you will get a consistent and stable way of administering your systems with Cockpit.

Getting started with Cockpit is as simple as enabling the cockpit socket and pointing a web browser at the Cockpit service. Because of Cockpit’s plug-in design, there are new tools being created all the time that you can add to your system’s Cockpit interface - _more on this later_.\
\
Once installed, point your remote web browser to port **`TCP 9090`** on the host. You can use the hostname or IP address. **`Port 9090`** is configured for `https` by default, although you can reconfigure that if you like to use `http`.

{% hint style="info" %}
Assuming you didn’t replace the self-signed certificate for Cockpit during the initial installation and configuration, you will be warned that the connection is not safe. To accept it anyway, and depending on your browser, you must select Advanced and agree to an exception to allow the browser to use the Cockpit service.
{% endhint %}

You will then be presented with a login screen. Here, you can enter your username and password as you would if you were logging in locally or via SSH. Use the `root` user, or a user with `sudo` privileges if you want to change your system configuration. A regular user can see, but cannot change most settings:

![Cockpit login screen for a RHEL server](<../../../../../../.gitbook/assets/image (150).png>)

![A view of the Cockpit interface once authenticated](<../../../../../../.gitbook/assets/image (181).png>)

The Cockpit dashboard contains a good set of features by default, and you can add many more later, on RHEL and Fedora systems. You begin seeing system activity related to CPU usage, memory and swap, disk input/output, and network traffic. Selections in the left navigation pane let you begin working with logs, storage, networking, user and group accounts, services, and many other features on your system.
