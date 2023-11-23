# dpkg

Simply put, **`dpkg`** is the yin to **`apt`**'s yang. We use **`apt`** for managing software from those big online repositories, leaving **`dpkg`** as your go-to when you want to get your hands on packages that are on your local machine.

Let's say you were surfing the web and snagged a **`.deb`** package with some software you fancy giving a whirl. If you...

1. Trust where it came from, and
2. Are sure it's not been messed with on its way to you...

You can't just use a simple **`apt install`** command to put it on your system. Nope, the job of installing, deleting, constructing, and overseeing **`.deb`** packages falls squarely on dpkg's shoulders. Let's dive into how it gets the job done.



### Installing a `.deb` File

Installing a **`.deb`** file is pretty simple. We use **`dpkg`** with the **`-i`** option:

```bash
sudo dpkg -i package_file_name.deb
```

{% hint style="info" %}
Note that in this example, the package is in the same working directory and so the full path is not provided. If you need a quick reminder on relative vs absolute paths, click here
{% endhint %}











{% hint style="info" %}
**Pro Tip**\
Many **`dpkg`** tasks can also be run through the more user-friendly **`apt`** despite the general use cases as described above. A quick google will show you everything you need to know - git it a go!
{% endhint %}
