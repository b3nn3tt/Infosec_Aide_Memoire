# Advanced Package Tool (apt)

### apt

Allow me to introduce you to a reliable mate - the Advanced Package Tool, or **`apt`** for short. **`apt`** can do two things:

1. It can fetch and install software from **online** **repositories** - it's most common use
2. **`apt`** can also install software from local files you already have on your computer or network

So, whether you want to get stuff from the internet or use something you've got saved, APT's got your back. It may seem a bit old-school compared to fancy graphical tools, but **`apt`** is incredibly versatile and quickly becomes a staple in most people's command-line toolkit. In most cases, **`apt`** teams up an action verb like **`update`** or **`install`**, and true to its name, does exactly what is says on the tin!

Here are some command examples you can experiment with:

| Command                             | Explanation                                                                                                                                                                                                        |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **`sudo apt update`**               | This updates the list of available software available in the target repositories. Note that this doesnt actually update the software, just the list                                                                |
| **`sudo apt-install package`**      | Pretty obvious - installs the named application(s)                                                                                                                                                                 |
| **`sudo apt-cache search package`** | Use this to search the list of available software for a match for any string you provide - matches are made by both package names and descriptions which is handy if you dont know the exact name of what you need |
| **`sudo apt-cache pkgnames`**       | This lists all the packages installed on the system                                                                                                                                                                |
| **`sudo apt remove package`**       | Use this to uninstall a named package, or list of packages                                                                                                                                                         |
| **`sudo apt purge package`**        | Uninstalls packages, however, whereas **`sudo apt remove`** will leave certain package artefacts like config files, **`purge`** nukes em all!!                                                                     |
| **`sudo apt upgrade`**              | Use this command to perform a mass update of all packages on the system. Note that this is normally preceeded by **`sudo apt update`** to ensure the upgrade provides the latest versions                          |
