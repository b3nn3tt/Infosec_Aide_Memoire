# Docker Registry

## **Docker Registry**

Before we begin exploiting a Docker Registry, we need to first understand not only how we interact with them, but as to why they are so lucrative for us pentesters. If you're familiar with Git, and services such as GitHub and Gitlab, this'll be a breeze. However, let's explain a bit further to ensure we're all on the same page.

Docker Registries, fundamentally, are used to store and provide published Docker images for use. Using repositories, creators of Docker images can switch between multiple versions of their applications and share them with other people with ease. Public registries such as DockerHub exist, however, many organisations using Docker will host their own "private" registry.

Take for example the RustScan DockerHub registry:

![The rustscan DockerHub registry](../../../.gitbook/assets/image%20%2876%29.png)

The developers have created a "tag" for every version of RustScan. As this is public, anyone can switch between the version of RustScan that they want to use with ease by downloading the image for the tag they want to use. 

You could simply run:

```text
 docker pull rustscan/rustscan:1.8.0 
```

This would result in the use of version 1.8.0 of RustScan.

Alternatively, or you could execute:

```text
 docker pull rustscan/rustscan:latest
```

This would result in pulling the most recent update. For a Docker repository to do this, the repository must store the data about every tag - **this is what we'll be exploiting**.

Since Docker images are essentially just instruction manuals, **they can be reversed to understand what commands took place when the image was being built** - this information is stored in layers...we will come onto unpacking these layers a little later.

