# Offensive Dorking

We can always rely on people being people. Computers merely do as they are told \(or more accurately, configured\), so all it takes is for a person to make a mistake, and we can capitalise on that. In this context, that mistake is configuring a system to be connected to the internet in an insecure way, and allowing Google to "index" its publicly accessible content - if Google can index it, you can access it.

So, let's see an example:

![](../../../../../.gitbook/assets/image%20%2870%29.png)

This search will find anything indexed by Google that contains the string `ViewerFrame?Mode=` in its URL. To be clear, this string is specific to Panasonic Webcams. So, any results you get from this search will reference publicly accessible web cams. For example, here is the rule of a simple search:

![The URL has been omitted to protect the idiotic](../../../../../.gitbook/assets/image%20%2881%29.png)

Now, I am not advocating that you go ahead and start clicking on every publicly accessible camera \(remember, accessing other peoples stuff is legally sketchy in many places... you have been warned\), but it's a nice, simple example that shows just how easy it is to gain access to systems that users \(or administrators\) have unwittingly left the door open to. And all we needed was Google...

