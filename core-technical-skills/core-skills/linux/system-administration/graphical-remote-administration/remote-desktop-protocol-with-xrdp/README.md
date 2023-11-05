# Remote Desktop Protocol with xrdp

Cockpit sets a high benchmark for browser-based Graphical Remote Administration, particularly suited to systems sans a full desktop environment. Yet, for systems equipped with a GUI, [xrdp](https://www.xrdp.org/) emerges as a compelling alternative. Embracing Microsoft's Remote Desktop Protocol (RDP), [xrdp](https://www.xrdp.org/) facilitates a graphical login from various RDP clients including:

* [FreeRDP](https://www.freerdp.com/)
* [rdesktop](http://www.rdesktop.org/)
* [NeutrinoRDP](https://github.com/neutrinolabs/NeutrinoRDP)
* Microsoft Remote Desktop Client (for [Windows](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/mstsc), [macOS](https://apps.apple.com/us/app/microsoft-remote-desktop/id1295203466?mt=12), [iOS](https://apps.apple.com/us/app/remote-desktop-mobile/id714464092) and [Android](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android\&hl=en\_GB\&gl=US))

Just as Windows-to-Windows Remote Desktop can, [xrdp](https://www.xrdp.org/) supports not only graphic remoting, but also

* Two-way clipboard transfer (text, bitmap, file)
* Audio redirection
* Drive redirection (mount local client drives on remote machine)

RDP transport is encrypted using TLS by default.
