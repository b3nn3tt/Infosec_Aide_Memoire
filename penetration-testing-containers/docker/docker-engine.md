# Docker Engine

When considering how we may exploit the Docker Engine, we need to first establish if the engine is **exposed.** In order to understand what I mean by exposed, we first need to look at UNIX Sockets.

## Unix Sockets

If I were to mention the word "socket", you would most likely think of networking, right? Well, you're not wrong in doing so. With that said, what is seldom discussed is UNIX sockets. Put simply, a UNIX socket accomplishes the same job as it's networking sibling - moving data. The key difference is that it all happens within the host itself, using the filesystem rather than networking interfaces/adapters; Inter-process Communication \(`IPC`\). 

It is an essential part to an operating system.

Due to the fact that UNIX sockets use the filesystem directly, you can use filesystem permissions to decide who, or what, can read/write \(file system permissions in this case are akin to firewall rules at the network level\). There was an interesting benchmark test between using both types of sockets for querying a MySQL database. Notice how there are an incredibly higher amount of queries performed when using UNIX sockets:

![](../../.gitbook/assets/image%20%2887%29.png)

Database systems such as [Redis](https://redis.io/) are known for their performance due to this reason.

### But what does this have to do with Docker?















