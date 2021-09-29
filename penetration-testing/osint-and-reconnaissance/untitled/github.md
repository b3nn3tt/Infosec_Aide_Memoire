# GitHub

[GitHub](https://github.com/), Inc. is a provider of Internet hosting for software development and version control using Git. It offers the distributed version control and source code management functionality of Git, plus its own features. Or, simply put, GitHub is where people upload their own code for collaborative working, and to also have an off-site store.

Again, we can always rely on people being people... All sorts of interesting things end up in GitHub. When you are working with Git, you often sync a local working directory with an online Git "Repository" \(an online code store for want of better description\). When you make changes to your code, you "push" the new, locally stored code up to GitHub. EVERYTHING that is contained in the sync'd folder will be uploaded, unless you manually specify which files should not be uploaded via the use of a `.gitignore` file. But guess what... people forget to do this all the time!

![Imagine my surprise...](../../../.gitbook/assets/image%20%2874%29.png)

So, it's always worth searching to see if your target maintains a GitHub repository. If they do, it is most certainly worth trawling through. It is possible that you may uncover the source code for a target application that could prove useful, although a savvy administrator _SHOULD_ make sure a repository private... however, there may be just a snippet of information that may be useful; a username, a password, an ip address, anything really.

Much like online search engines, the search mechanism in GitHub also supports operators. Let's take a quick look:

![Use of the operator filename:](../../../.gitbook/assets/image%20%28104%29.png)

Here, we can see that the operator `filename:` was used to search for any file with the word users in the name. The results reveal a single result - `xampp.users:` 

![Interesting search results](../../../.gitbook/assets/image%20%28126%29.png)

Even with a single result, we may have found something very interesting. [XAMPP](https://www.apachefriends.org/index.html) is a web application development environment. Let’s check the contents of the file:

```text
trivera:$apr1$A0vSKwao$GV3sgGAj53j.c3GkS4oUC0
```

That sure looks like credentials to me...

This manual approach will work best on small repos. For larger repos, we can use several tools to help automate some of the searching, such as [Gitrob](https://github.com/michenriksen/gitrob) and [Gitleaks](https://github.com/zricethezav/gitleaks). [Recon-ng](https://github.com/lanmaster53/recon-ng) also has several modules for searching GitHub.

{% hint style="info" %}
Most of these tools require an access token to use the source code hosting provider’s API
{% endhint %}

