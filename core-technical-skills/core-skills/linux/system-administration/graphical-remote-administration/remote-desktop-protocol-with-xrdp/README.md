# Remote Desktop Protocol with xrdp

Cockpit is the gold standard of Graphical Remote Administration tools as it presents a user friendly interface for systems that aren't necessarily running a full desktop environment. However, if your remote target is running a GUI, then you have another option in `xrdp`.

`xrdp` provides a graphical login to remote machines using RDP,  Microsoft's Remote Desktop Protocol. `xrdp` accepts connections from variety of RDP clients such as:&#x20;

* [FreeRDP](https://www.freerdp.com/)\

* [rdesktop](http://www.rdesktop.org/)\

* [NeutrinoRDP](https://github.com/neutrinolabs/NeutrinoRDP)\

* Microsoft Remote Desktop Client (for [Windows](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/mstsc), [macOS](https://apps.apple.com/us/app/microsoft-remote-desktop/id1295203466?mt=12), [iOS](https://apps.apple.com/us/app/remote-desktop-mobile/id714464092) and [Android](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android\&hl=en\_GB\&gl=US))

Just as Windows-to-Windows Remote Desktop can, `xrdp` supports not only graphic remoting, but also

* Two-way clipboard transfer (text, bitmap, file)\

* audio redirection\

* drive redirection (mount local client drives on remote machine)

RDP transport is encrypted using TLS by default.

