# The Harvester

If you are looking for a tool to achieve the same outcome as FOCA, but from a Linux machine, then the Harvester is the tool for you. The Harvester is a commandline tool that is readily available via most package managers, and rather helpfully comes preinstalled in Kali Linux.

The options are as follows:

| Option | Description |
| :--- | :--- |
| `-b` | Data Source - Available sources include google, bing, linkedin, twitter, pgp and more |
| `-c` | Perform DNS Brute Force for Domain |
| `-d` | Target Domain |
| `-e` | Use a specific DNS Server |
| `-f` | Save results in both .XML and .HTML format |
| `-h` | Leverage the Shodan database |
| `-l` | Limits results to the number specified |
| `-n` | Perform reverse DNS on the target |
| `-s` | Start is result number - Default is zero |
| `-t` | Perform DNS TLD discovery |
| `-v` | Verify hostname via DNS |

Let's see an example:

```text
theHarvester -d megacorpone.com -b google
```

![Output from theHarvester](../../../.gitbook/assets/image%20%2898%29.png)

We found some email addresses, and some new subdomains of megacorpone.

{% hint style="info" %}
Adding findings to your OSINT dossier is an iterative process - you may discover new information that requires you to double back and run things again in light of new information
{% endhint %}

