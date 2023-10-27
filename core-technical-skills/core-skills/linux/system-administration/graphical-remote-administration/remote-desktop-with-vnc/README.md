# Remote Desktop with vnc

Virtual Network Computing, or VNC, is a connection system that allows you to use your keyboard and mouse to interact with a graphical desktop environment on a remote server. It makes managing files, software, and settings on a remote server easier for users who are not yet comfortable with the command line.

In this example, you’ll set up a VNC server with [TightVNC](https://www.tightvnc.com/) on an Ubuntu server and connect to it securely through an SSH tunnel. Then, you’ll use a VNC client program on your local machine to interact with your server through a graphical desktop environment.

To establish remote access, you can use any of the following client applications:

|                                                                            | Windows | Linux | MacOS |
| -------------------------------------------------------------------------- | ------- | ----- | ----- |
| [TightVNC](https://www.tightvnc.com/)                                      | Y       | Y     | N     |
| [RealVNC](https://www.realvnc.com/en/)                                     | Y       | Y     | Y     |
| [UltraVNC](https://www.uvnc.com/)                                          | Y       | N     | N     |
| [Screen Share](https://support.apple.com/en-gb/guide/mac-help/mh14066/mac) | N       | N     | Y     |
| [Vinagre](https://www.linuxlinks.com/vinagre/)                             | N       | Y     | N     |
| [krdc](https://apps.kde.org/en-gb/krdc/)                                   | N       | Y     | N     |
