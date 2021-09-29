# twofi

[twofi](https://digi.ninja/projects/twofi.php) scans a user’s Twitter feed and generates a personalized wordlist used for password attacks against that user. While we would not run attacks against a target during passive reconnaissance, we can run this tool against any Twitter accounts we have identified to prepare a wordlist for when its needed.

{% hint style="info" %}
Twofi requires a valid Twitter API key.
{% endhint %}



## Installing twofi

The only ruby gem that probably isn't installed by default is the twitter one. To install this, run:

```text
bundle install
ruby twofi.rb
```

![twofi installation after download](../../../../.gitbook/assets/image%20%2888%29.png)

Or, make the script executable, then run it directly:

```text
chmod a+x twofi.rb
./twofi.rb
```

twofi v1 used the now removed Twitter search feature, which did not require any authentication. twofi v2 now uses the new API, which requires you to have a Twitter account and apply for API keys. The process is simple and instant, no cash, no waiting for human approval, so no big deal.

{% hint style="info" %}
You need to go to [https://apps.twitter.com/](https://apps.twitter.com/) and fill in your details. This will give you a pair of keys which you then need to put into the twofi.yml config file
{% endhint %}

At the moment, the script expects the config file to be in the same directory as twofi is being ran from. If this is not the case, you can tell it where the config file is by using the `--config` parameter. Then you can run twofi by either using ruby, or making it executable and running it directly:

```text
#Execution via ruby
ruby twofi.rb

#Direct execution
chmod a+x twofi.rb
./twofi.rb
```

{% hint style="info" %}
twofi is now available in the Kali Linux default repository. So, you can install the tool with a simple `apt install`
{% endhint %}



## Using twofi

Usage is fairly simple, you can specify search terms or usernames either on the command line as comma separated lists, or through files which you pass in. If you are specifying the terms or users on the command line you cannot have a space between the comma and the words, i.e. this is **good**:

**`term1,term2,term3`**

and this is **bad**:

**`term1, term2, term3`**

This is because of the way the command line arguments are parsed, the space is taken to mean a new parameter. If you are using files**,** each term/username should be on its own line.

When specifying usernames, you do not need the @ symbol. If you pass it, it will be stripped off when used anyway, so save yourself some typing.

The `--count` option allows you to request the number of times each word is used. This might help if you only have a limited number of attempts to use the words and so need to decide which are really worth trying.

At the moment there is nothing for the script to be verbose about so the verbose flag does nothing.

![twofi command options](../../../../.gitbook/assets/image%20%2879%29.png)





