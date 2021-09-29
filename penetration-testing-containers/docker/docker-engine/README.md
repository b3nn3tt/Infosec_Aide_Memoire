# Docker Engine

When considering how we may exploit the Docker Engine, we need to first establish if the engine is **exposed.** In order to understand what I mean by exposed, we first need to look at UNIX Sockets.

## Unix Sockets

If I were to mention the word "socket", you would most likely think of networking, right? Well, you're not wrong in doing so. With that said, what is seldom discussed is UNIX sockets. Put simply, a UNIX socket accomplishes the same job as it's networking sibling - moving data. The key difference is that it all happens within the host itself, using the filesystem rather than networking interfaces/adapters; Inter-process Communication \(`IPC`\). 

It is an essential part to an operating system.

Due to the fact that UNIX sockets use the filesystem directly, you can use filesystem permissions to decide who, or what, can read/write \(file system permissions in this case are akin to firewall rules at the network level\). There was an interesting benchmark test between using both types of sockets for querying a MySQL database. Notice how there are an incredibly higher amount of queries performed when using UNIX sockets:

![](../../../.gitbook/assets/image%20%2894%29.png)

Database systems such as [Redis](https://redis.io/) are known for their performance due to this reason.

### But what does this have to do with Docker?

Users interact with Docker by using the Docker Engine. For example, commands such as `docker pull` or `docker run` will be executed by the use of a socket - this can either be a UNIX or a TCP socket, but by default, it is a UNIX socket. This is why you must be apart of the "docker" group to use the docker command \(remembering that UNIX sockets can use file permissions here!\) as illustrated below:

 The user "**cmnatic**" is in the "**docker**" ****group:

![](../../../.gitbook/assets/image%20%2877%29.png)

 ...and can therefore run commands like `docker images`:

![](../../../.gitbook/assets/image%20%2870%29.png)

In contrast, the user "**notcmnatic**" is **not** in the "**docker**" group, and therefore cannot run Docker commands due to lack of permissions to the Docker socket:

![](../../../.gitbook/assets/image%20%2891%29.png)

![](../../../.gitbook/assets/image%20%2873%29.png)

Developers love to automate, and this is proven nonetheless with Docker. Whilst Docker uses a UNIX socket by default, a developer may wish to remotely execute Docker commands, such as in Docker management tools like [Portainer](https://www.portainer.io/), or via DevOps applications like [Jenkins](https://www.jenkins.io/), to test their program.

To achieve this, the daemon must use a TCP socket instead of a UNIX socket, permitting data for the Docker daemon to be communicated via a network interface, ultimately **exposing** it to the network, potentially rendering it more susceptible to exploitation...









