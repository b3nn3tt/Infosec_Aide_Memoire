# Installation and Configuration

This example assumes you are installing on a Debian based system, such as Ubuntu.&#x20;

## Install xrdp

```
udo apt update
sudo apt upgrade
sudo apt install xrdp
```

##

## Configure xrdp

```
sudo mkdir /etc/polkit-1/rules.d
sudo touch /etc/polkit-1/rules.d/02-allow-colord.rules
sudo nano /etc/polkit-1/rules.d/02-allow-colord.rules
```

Copy the following into your newly created file:

```
polkit.addRule(function(action, subject) {
   if ((action.id == "org.freedesktop.color-manager.create-device" ||
        action.id == "org.freedesktop.color-manager.create-profile" ||
        action.id == "org.freedesktop.color-manager.delete-device" ||
        action.id == "org.freedesktop.color-manager.delete-profile" ||
        action.id == "org.freedesktop.color-manager.modify-device" ||
        action.id == "org.freedesktop.color-manager.modify-profile") &&
        subject.isInGroup("vglusers")) {
      return polkit.Result.YES;
   }
});
```

##

## Enable the xrdp Service

```
sudo systemctl enable xrdp
sudo systemctl enable xrdp-sesmanq
sudo systemctl restart xrdp
sudo systemctl restart xrdp-sesmanq
```

###

## Restart your system

```
sudo shutdown -r now
```

You can find alternative methods for this process at the [xrdp](https://www.xrdp.org/) [github page](https://github.com/neutrinolabs/xrdp).
