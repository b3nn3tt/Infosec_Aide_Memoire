# Shodan

 [Shodan](https://www.shodan.io) is “_the world's first search engine for Internet-connected device_s”.

As we gather information on our target, it is important to remember that traditional websites are just one part of the Internet. Shodan is a search engine that crawls devices connected to the Internet including, but not limited to, the World Wide Web. This includes the servers that run websites but also devices like routers and IoT devices. To put it another way, Google and other search engines look for **Web server content** only, while Shodan searches for Internet-connected devices, interacts with them, and displays information about them.

{% hint style="info" %}
Shodan blurs the lines with passive and active reconnaissance. From our perspective, we are remaining passive as we are merely querying a third party database, just like any other search engine. But from the target's perspective, they have been actively probed by Shodan at some point
{% endhint %}

Let’s start by using Shodan to search for **hostname:megacorpone.com**:

![](../../../../.gitbook/assets/image%20%28140%29.png)

In this case, Shodan lists the IPs, services, and banner information. All of this is gathered without interacting with the client’s web site. This information gives us a snapshot of our target’s Internet footprint. For example, there are eight servers running SSH, and we can drill down on this to refine our results by clicking on SSH under Top Services:

![](../../../../.gitbook/assets/image%20%28110%29.png)

Based on Shodan’s results, we know exactly which version of OpenSSH is running on each server. If we click on an IP address, we can retrieve a summary of the host:

![](../../../../.gitbook/assets/image%20%28125%29.png)

We can view the ports, services, and technologies used by the server on this page. Shodan will also reveal if there are any published vulnerabilities for any of the identified services or technologies. This information is invaluable when determining where to start when we move to active testing.

