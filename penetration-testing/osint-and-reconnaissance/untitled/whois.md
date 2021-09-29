# whois

`whois` is a TCP service, tool, and a type of database that can provide information about a domain name, such as the name server and registrar. This information is often public since registrars charge a fee for private registration.

{% hint style="info" %}
Most versions of Linux/UNIX include the WHOIS client. It is included in MacOS, but not Windows by default, although sysinternals has it should you want to install it
{% endhint %}

We can gather basic information about a domain name by executing a standard forward search, passing the domain name `hbcomputersecurity.co.uk` into the `whois` client:

```text
whois hbcomputersecurity.co.uk
```

![An example of the whois command](../../../.gitbook/assets/image%20%2888%29.png)

{% hint style="info" %}
In this example, the domain was registered with [godaddy](https://uk.godaddy.com/), an internet registrar. They offer privacy by listing themselves as the registrar, rather than the actual owner of the domain, but if you run `whois` against any other domain, you may get different results
{% endhint %}

In addition to this standard forward lookup, which gathers information about a DNS name, the `whois` client can also perform reverse lookups. Assuming we have an IP address, we can perform a reverse lookup to gather more information about it:

```text
whois 8.8.8.8
```

![](../../../.gitbook/assets/image%20%2873%29.png)

The results of the reverse lookup gives us information on who is hosting the IP address. This information could be useful later, and as with all the information we gather, we will add this to our notes.



