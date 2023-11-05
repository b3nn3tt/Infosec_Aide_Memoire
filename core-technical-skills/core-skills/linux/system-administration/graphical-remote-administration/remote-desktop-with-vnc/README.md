# Remote Desktop with vnc

Virtual Network Computing, or VNC, presents a platform that enables the use of a remote server's graphical desktop environment from another computer. It translates your keyboard and mouse actions to the server, simplifying the management of files, applications, and system preferences for those less acquainted with command-line operations.

In this guide, we will walk through setting up a VNC server using [TightVNC](https://www.tightvnc.com/) on an Ubuntu server, demonstrating how to establish a secure connection via an SSH tunnel. On your local computer, you'll deploy a VNC client to navigate your server's graphical interface as if you were physically present.

The following VNC client applications are compatible for establishing a remote connection:

|                                                                            | Windows | Linux | MacOS |
| -------------------------------------------------------------------------- | ------- | ----- | ----- |
| [TightVNC](https://www.tightvnc.com/)                                      | Y       | Y     | N     |
| [RealVNC](https://www.realvnc.com/en/)                                     | Y       | Y     | Y     |
| [UltraVNC](https://www.uvnc.com/)                                          | Y       | N     | N     |
| [Screen Share](https://support.apple.com/en-gb/guide/mac-help/mh14066/mac) | N       | N     | Y     |
| [Vinagre](https://www.linuxlinks.com/vinagre/)                             | N       | Y     | N     |
| [krdc](https://apps.kde.org/en-gb/krdc/)                                   | N       | Y     | N     |
