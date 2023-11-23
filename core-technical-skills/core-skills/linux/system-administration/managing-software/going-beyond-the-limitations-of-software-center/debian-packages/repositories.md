# Repositories

So far I've really only passively mentioned repositories, so i'd like to take a moment to go over them. Repositories are like digital storehouses for software for your computer. They're online collections of programs, updates, and all sorts of tech goodies. When you want to install new software or update existing programs, your computer checks these repositories to see what's available. Think of it like a massive library where you can borrow the latest books (or software) for your system.&#x20;

Different Linux distributions have their own repositories, and you can add or remove them to access a wide range of software tailored to your needs.

You've got the reins when it comes to deciding which repositories **`apt`** commands tap into. It's all in the setup files stashed away in the **`/etc/apt`** directory. The top dog among these files is **`sources.list`**, and it's the one **`apt`** relies on to figure out where to scout for software. Normally, you'll find a bunch of lines in there with comments describing what's what, and maybe a few extras for optional repositories. But if you're curious about what an uncluttered version looks like with only the active repositories listed, go ahead and peek at the one on your own machine:

```bash
cat /etc/apt/sources.list
```

<figure><img src="../../../../../../../.gitbook/assets/image (232).png" alt=""><figcaption><p>Contents of /etc/apt/sources.list</p></figcaption></figure>

{% hint style="info" %}
If you're up for it, third parties have the option to add their repository details as files in the **`/etc/apt/sources.list.d`** directory
{% endhint %}



### Personal Package Archives

There might be times when you fancy adding a personal repository to your **`apt`** setup manually. It could be for handling your own software project or grabbing something that's not in the usual repositories. You can achieve this through **Personal Package Archives** (**PPAs**).

{% hint style="info" %}
Be extra cautious and double-check that you trust the sources you're adding, as these repositories aren't screened for malware or managed as meticulously as the mainstream ones
{% endhint %}

Now I know what your first question will be...

> _"Where do I find PPA's?"_

Start by searching online for the software you want to install, along with the term "PPA" or "Personal Package Archive." For example, if you're looking for the latest version of a video editing tool called "MyVideoApp," you might search for "MyVideoApp PPA".

Many PPAs have dedicated websites or pages on platforms like [**Launchpad**](https://launchpad.net/) (common for Ubuntu PPAs). These pages provide detailed information about the PPA, including its name, description, and the software it contains. For example, a PPA page for the "MyVideoApp" software might look like this:

```bash
PPA Name: myvideoapp/ppa
Description: Unleash your video editing skills with MyVideoApp!
Packages: myvideoapp, myvideoapp-dev, myvideoapp-docs
```

There are also community forums. Linux user forums and communities often discuss and share information about PPAs. You may find recommendations and links to PPAs in these discussions.

Generally though, you will usually find PPA's as the need arises.&#x20;

Let's say you want to install an application; you go onto [**Software Centre**](../../managing-software-from-the-desktop.md) or search with **`apt`** and find nothing. So, you get your best google-fu on and you find a website for the software you want to install - in this case, let's say it's **skype**:

<figure><img src="../../../../../../../.gitbook/assets/Screenshot 2023-11-23 at 16.57.14.png" alt=""><figcaption><p>Search Result for "skype ppa"</p></figcaption></figure>

As you can see, we get some results. Clicking on the top one, we are taken to a site that provides the details for a PPA, which, when added using the provided commands, allows us to install **skype** using **`apt`**:

<figure><img src="../../../../../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

To add a repository, we can use **`apt`**. Let's w**alk through the process step-by-step:**

1. **Find the PPA**\
   First, you must identify the PPA you want to add. You can often find the PPA's information on websites, forums, or the developer's documentation.
2. **Add the PPA**\
   Use the **`add-apt-repository`** command, followed by the PPA's URL or name:

```bash
sudo add-apt-repository ppa:example/ppa
```

3. **Update APT**\
   After adding the PPA, update your package list:

```bash
sudo apt update
```

4. **Install Software**\
   Once the update is complete, you can install software from the newly added PPA using **`apt`** just as you would any other piece of software

{% hint style="info" %}
<mark style="color:red;">**A Word of Caution**</mark>\
In the screenshot above, you'll notice the commands come with some certificate info for encryption. This stuff matters because we rely on **`apt`** to make sure the software packages we get are the exact ones from the repository. If those keys can't be verified, well, there's no guarantee, and it's best to steer clear of that software
{% endhint %}

###

### Removing Unwanted PPA's

When you add a Personal Package Archive (PPA) to your system, it gets added as a configuration file in the **`/etc/apt/sources.list.d/`** directory. Each PPA typically has its own file named with the PPA's name and a **`.list`** extension.

At some point, you're likely to want to uninstall the software and remove the PPA as it will be redundant. So, to get rid of a PPA, follow these steps:

1. **List PPAs**\
   First, you can list the PPAs currently added to your system using the following command:

```bash
ls /etc/apt/sources.list.d/
```

2. **Identify the PPA**\
   Look for the PPA file that corresponds to the PPA you want to remove. The file names are usually in the format **`ppa-name-ubuntu-version.list`**
3. **Remove the PPA**\
   To remove the PPA, you can use the **`add-apt-repository`** command with the **`--remove`** option, followed by the PPA URL or name:

```
sudo add-apt-repository --remove ppa:example/ppa
```

4. **Update APT**\
   After removing the PPA, it's a good practice to update your package list with:

```bash
sudo apt update
```

**Optional Extra: Delete the PPA File**\
If you want to completely remove the PPA file, you can use the **`rm`** command. For example, if the PPA file is named **`example-ubuntu-ppa.list`**, you can delete it with:

```bash
sudo rm /etc/apt/sources.list.d/example-ubuntu-ppa.list
```
