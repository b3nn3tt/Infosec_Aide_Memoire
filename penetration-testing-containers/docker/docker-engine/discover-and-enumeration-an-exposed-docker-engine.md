# Discover and Enumeration an Exposed Docker Engine

Like almost all network discovery and enumeration, we start with `nmap`. By default, the engine will run on port **TCP 2375**:

```text
nmap -sS -sV -p 2375 [TARGET-IP]
```

![Discovery of an exposed docker engine running on the default port](../../../.gitbook/assets/image%20%28108%29.png)

In this case, we can see that the engine is exposed across the network!

{% hint style="info" %}
Of course, you can configure the Docker Engine to bind to any available port, meaning that scanning solely on the default TCP port runs the risk of non-discovery. The example here is limited for illustration purposes, but always ensure you thoroughly scan and enumerate all ports on a target
{% endhint %}

