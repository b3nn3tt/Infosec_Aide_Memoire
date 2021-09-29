# Docker

So, what IS [Docker](https://www.docker.com/)?

Starting in 2013, Docker was introduced to solve the costly and time-consuming process of application development and service delivery. Docker employs what is currently a "hot potato" topic for developers; **containerisation**. This technology separates applications into their own bespoke environment, or “container”, where they share the resources of, but interact with, the host operating system independently of each other.

### Docker

* Is extremely portable; if a computer can run Docker, it can run a Docker container. This means that developers only have to write the application once for multiple devices - a very big headache solved!
* Has a considerably less resource usage per-container then Virtual Machines \(VMs\) I.e. RAM and CPU
* Allows you to set up a complex environment in a few simple steps through “Dockerfiles” \(more on this shortly\)
* Is, most importantly, very lucrative to a pentester - containerisation has been so widely adopted in information technology today, its too vast a technology to ignore

### **What are Containers, and WHY are they used?**

Containers share computing resources with, but remain isolated enough to not conflict with, one another via the **Docker Engine**. These containers don't run a fully-fledged operating system, unlike a VM. 

Let's look at the diagram below for a better picture:

![A high-level concept of Docker](../../.gitbook/assets/image%20%28132%29.png)

We can see three containers running their own applications with no virtualisation. The three applications are isolated from one another, but use the main operating system's resources.

In comparison, running these applications in virtual machines:

![A high-level concept of Virtualisation](../../.gitbook/assets/image%20%28108%29.png)

 The "_Guest Operating System_" is where the resources are used up.

For example, a recommended minimum install size of Ubuntu is **20gb**. If you were to run three applications in VM's for isolation, you'd require **60gb** of storage. A Ubuntu Docker image has the base size of around **180MB**. Containers can share base images too! Clearly, it is an extremely space-efficient solution.

### What are Docker Images

Whilst we don't need an encyclopaedic knowledge of how containers work, we do need to understand some basic principles, such as Docker images. Docker containers are created from Docker images; consider these images as instruction manuals telling you how to assemble a piece of furniture. These files contain commands such as `RUN` and `COPY`, that will be executed by the container. `RUN` commands will execute system commands such as `apt-get` or `ls /home/`.

