# linked2username

[linkedin2username](https://github.com/initstring/linkedin2username) is a python script for generating username lists based on LinkedIn data. It requires valid LinkedIn credentials, and depends on a LinkedIn connection to individuals in the target organization. The script will output usernames in several different formats.

This is a pure web-scraper, no API key required. You use your valid LinkedIn username and password to login, it will create several lists of possible username formats for all employees of a company you point it at.

Use an account with a lot of connections, otherwise you'll get crappy results. Adding a couple connections at the target company should help - this tool will work up to third degree connections. Note that LinkedIn will cap search results to 1000 employees max. You can use the features `--geoblast` or `--keywords` to bypass this limit. Look at help below for more details.  
  
Here's what you get:

* `first.last.txt`: Usernames like Joe.Schmoe 
* `flast.txt`: Usernames like JSchmoe 
* `firstl.txt`: Usernames like JoeS 
* `first.txt`: Usernames like Joe 
* `lastf.txt`: Usernames like SchmoeJ 
* `rawnames.txt`: Full name like Joe Schmoe

Optionally, the tool will append @domain.xxx to the usernames.



## linked2username Usage

You'll need to provide the tool with LinkedIn's company name. You can find that by looking at the URL for the company's page. It should look something like `https://linkedin.com/company/uber-com`. It may or may not be as simple as the exact name of the company.

Here's an example to pull all employees of Uber:

```text
python linkedin2username.py myname@email.com uber-com
```

Here's an example to pull a shorter list and append the domain name @uber.com to them:

```text
python linkedin2username.py myname@email.com uber-com -d 5 -n 'uber.com'
```

