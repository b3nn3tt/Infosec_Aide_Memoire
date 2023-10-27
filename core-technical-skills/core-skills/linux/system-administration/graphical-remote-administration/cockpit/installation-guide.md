# Installation Guide

The following information can be found in greater deal in the online [Cockpit documentation](https://cockpit-project.org/running.html#fedora), and the deployment guide can be found [here](https://cockpit-project.org/guide/latest/).

## **Fedora**

Cockpit comes installed by default in Fedora Server. To install Cockpit on other variants of Fedora use the following commands. For the latest versions use COPR.

```
#Install cockpit:
sudo dnf install cockpit

#Enable cockpit:
sudo systemctl enable --now cockpit.socket
Created symlink /etc/systemd/system/sockets.target.wants/cockpit.socket

#Open the firewall if necessary:
sudo firewall-cmd --add-service=cockpit
sudo firewall-cmd --add-service=cockpit --permanent
```



## R**ed Hat Enterprise Linux**

Cockpit is included in Red Hat Enterprise Linux 7 and later.

```
#On RHEL 7, enable the Extras repository. RHEL 8 does not need any non-default repositories.
sudo subscription-manager repos --enable rhel-7-server-extras-rpms

#Install cockpit:
sudo yum install cockpit

#Enable cockpit:
sudo systemctl enable --now cockpit.socket

#On RHEL 7, or if you use non-default zones on RHEL 8, open the firewall:
sudo firewall-cmd --add-service=cockpit
sudo firewall-cmd --add-service=cockpit --permanent
```



## **Fedora CoreOS**

The standard Fedora CoreOS image does not contain Cockpit packages.

```
#Install Cockpit packages as overlay RPMs:
rpm-ostree install cockpit-system cockpit-ostree cockpit-podman

#Depending on your configuration, you may want to use other extensions as well, such as cockpit-kdump or cockpit-networkmanager. If you have a custom-built OSTree, simply include the same packages in your build.

#Reboot
sudo shutdown -r now

#Run the Cockpit web service with this privileged container (as root):
podman pull cockpit/ws
podman container runlabel --name cockpit-ws RUN cockpit/ws

#Make Cockpit start on boot:
podman container runlabel INSTALL cockpit/ws
systemctl enable cockpit.service
```

Steps 3 and 4 are optional if the CoreOS machine will only be connected to from another host running Cockpit. Afterward, use a web browser to log into port **`TCP 9090`** on your host IP address as usual.



## **Project Atomic**

Connect to an Atomic Host from another instance of Cockpit with the Add Server dashboard UI. Alternatively you can access Cockpit directly on the Atomic Host if SSH password authentication is enabled:

```
#Run the Cockpit web service container:
sudo atomic install cockpit/ws
sudo atomic run cockpit/ws
```



**CentOS**

Cockpit is included in CentOS 7.x:

```
#Install cockpit:
sudo yum install cockpit

#Enable cockpit:
sudo systemctl enable --now cockpit.socket

#Open the firewall if necessary:
sudo firewall-cmd --permanent --zone=public --add-service=cockpit
sudo firewall-cmd --reload
```



## **Debian**

Cockpit is included in Debian unstable and in backports for 9 (Stretch):

```
#For Debian 9 you have to enable the backports repository:
echo 'deb http://deb.debian.org/debian stretch-backports main' > \ /etc/apt/sources.list.d/backports.list
apt-get update

#Install the package:
sudo apt-get install cockpit
```



## **Ubuntu**

Cockpit is included in Ubuntu 17.04 and later, and available as an official backport for 16.04 LTS and later. Backports are enabled by default, but if you customized apt sources you might need to enable them manually.

```
#Install the package:
sudo apt-get install cockpit
```
