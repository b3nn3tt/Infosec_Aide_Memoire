# Shared Namespace

Before we go much further, let's quickly go over how Docker isolates containers from one another real quick...

![High-level representation of docker container isolation](../../../../.gitbook/assets/image%20%28104%29.png)

As you have no doubt discovered by now, containers have their own networking capabilities and file storage. They achieve this by using three components of the Linux kernel:

* Namespaces 
* Cgroups 
* OverlayFS

Here, we are going to focus on **namespaces**, after all, they lay at the heart of it. Namespaces essentially segregate system resources such as processes, files and memory away from other namespaces. Every process running on Linux will be assigned two things:

* A namespace 
* A Process Identifier \(PID\)

Leveraging namespaces is how containerisation is achieved. Processes can only "see" the process that is in the same namespace - no conflicts \(_in theory_\). Consider Docker... Every new container will run as a new namespace, although the container may be running multiple applications \(and in turn, multiple processes\).

Let's prove the concept of containerisation. We will compare the number of processes there are in a Docker container that hosts a webserver versus a host operating system at the time:

![FULL HOST OS](../../../../.gitbook/assets/image%20%2882%29.png)

Note some useful information highlighted in red. On the very left, we can see the system user the process is running as, then the processes number \(PID\). There are a few more columns that, for this task, aren't worth explaining. But notice in the last column, the command that is running. I've highlighted a Docker command running, and an instance of Google Chrome running. As you can see, there are LOTS of processes running...

![DOCKER CONTAINER](../../../../.gitbook/assets/image%20%2870%29.png)

By contrast, the Docker container is far less “busy”. This is a dead giveaway that you are in a container.

### But why do we care?

Simply put, the process ID with a value of 0 \(or **`PID 0`**\) is the process that starts when a system boots. Processes then number incrementally as they are spawned \(by another process\), so naturally, the first process POST boot will be **`PID 1`**. This process is the systems init, which in the latest versions of Ubuntu \(and many other distros\) use **systemd**. All subsequent processes that run will therefore be controlled by systemd.

We can use PID 1's namespace on an operating system to escalate our privileges.

Whilst containers are designed to use these namespaces to isolate from another, they can instead coincide with the host computers processes rather than remain isolated from them. This gives us a potential opportunity to escape!











