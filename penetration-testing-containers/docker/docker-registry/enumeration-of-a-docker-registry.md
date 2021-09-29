# Enumeration of a Docker Registry

## **Interacting with a Docker Registry**

As with any system that we are going to be penetration testing, we need to enumerate the services running to understand any potential entry points. ****Docker Registry runs on **`TCP 5000`** by default, however, this can be easily changed, so it is worth confirming via with a nmap scan like so:

```text
nmap -sV -p- [TARGET-IP]
```

![nmap scan results, showing a Docker registry running on default TCP 5000, and another on TCP 7000](../../../.gitbook/assets/image%20%2891%29.png)

{% hint style="info" %}
Not only is nmap capable of discovering the Docker Registry, but also the API version - this is important to note for how we will interact with it
{% endhint %}

The Docker Registry is a **JSON** endpoint, so we cannot just simply interact with it like we would a normal website - we will have to query it. Whilst this can be done via the terminal or browser, or via dedicated tools such as [Postman](https://www.postman.com/downloads/) or [Insomnia](https://insomnia.rest/download) which are much better suited for the job.

We will be using **Postman** from herein.

\*\*\*\*

## **Discovering Repositories**

We will be using the target [http://docker-rodeo.thm](http://docker-rodeo.thm) for illustration.

We need to send a `GET` request to `http://docker-rodeo.thm:5000/v2/_catalog` to list all the repositories registered on the registry:

![A crafted GET request to the target Docker Registry](../../../.gitbook/assets/image%20%28101%29.png)

 As you can see, we're given a response of three repositories. For now, we are only going to focus on `cmnatic/myapp1`.

Before we can begin analysing a repository, we need two key pieces of information:

1. The repository name ****
2. Any repository tag\(s\) published

We currently have the repository name, `cmnatic/myapp1`. Now, we need to list all tags that have been published. Every repository will have a minimum of one tag. This tag is the "_latest_" tag, but there may be many tags, all with different code \(for example, major software versions\), or even two tags for "**production**" and "**development**".

We will craft a `GET` request to the registry to query all published tags. For our application, our request would look like so: 

```text
http://docker-rodeo.thm:5000/v2/cmnatic/myapp1/tags/list
```

![A crafted GET request to determine tags](../../../.gitbook/assets/image%20%2869%29.png)

Note here we have three tags? That **"notsecure"** tag sure sounds interesting...

We now have both pieces of information required to retrieve the manifest files of the image for analysis.



## Grabbing the Data

With these two important pieces of information about a repository known, we can enumerate that specific repository for a manifest file. This manifest file contains various pieces of information about the application, such as size, layers and other information. 

We are going to grab the manifest file for the "**notsecure**" tag via the following **GET** request:

```text
http://docker-rodeo.thm:5000/v2/cmnatic/myapp1/manifests/notsecure
```

![Grabbing the manifest file](../../../.gitbook/assets/image%20%2896%29.png)

Note the response - specifically the "history" key \(as shown\); albeit slightly hard to read, we have a command that was executed during the image building stage stored in plaintext;  
  
`echo \\\"here's a flag\\\" \\u003e /root/root.txt\"]`   
  
In this image, it's a string insert into `/root/root.txt` on the container. Imagine if this was a valid password!...

As you can see, we are able to query the Docker registry and the data contained within without needing to authenticate.

