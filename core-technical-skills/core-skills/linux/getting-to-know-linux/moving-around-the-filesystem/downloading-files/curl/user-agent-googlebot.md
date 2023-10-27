# User-Agent: Googlebot

I have seen examples where a specific Agent-String was required to perform some kind of action. It is a common tactic in Capture the Flag exercises, but it is also actively used out in production systems.

The following screenshot depicts such a requirement:

![Access is restricted to the resource by User-Agent string](<../../../../../../../.gitbook/assets/image (206).png>)

Using `curl`, we can circumnavigate this restriction to access the `robots.txt` file:

```
curl --user-agent "Googlebot" http://10.11.1.39/robots.txt
```

![The resource is successfully accessed](<../../../../../../../.gitbook/assets/image (41).png>)
