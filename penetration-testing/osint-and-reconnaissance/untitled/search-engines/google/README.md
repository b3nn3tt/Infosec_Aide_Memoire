# Google

Google is, by any measure, the dominant search engine of choice. So, when you are performing your OSINT reconnaissance, you will no doubt end up here. The obvious thing to say straight out the gates is that as the dominant engine, Google is saturated with information - finding the things you are looking for can be a frustrating exercise. However, we can help to reduce the effort a little by using a method known as **Google Dorking**.

## Google Dorking

According to [McAfee](https://www.mcafee.com/blogs/enterprise/google-dorking/):

> Google Dorking is a search technique that enables hackers to gain access to information that corporations and individuals did not intend to make publicly available. Using this technique, hackers are able to identify vulnerable systems and can recover usernames, passwords, email addresses, and even credit card details. Used effectively, Google Dorking is a valuable hacking shortcut to finding systems and data of interest.

That all sounds exciting, doesn't it! But in plain English, what does it mean?

Simply put, Google \(and many other search engines for that matter\) support the use of **search operators**, or "filters", to help to shape your search to be more efficient. Often, said operators are undocumented, and using them can trigger an error from Google, who will be suspicious of your usage:

![Paranoid Google...](../../../../../.gitbook/assets/image%20%28109%29.png)

So, in practice, all you need to do is enter a search into Google as you ordinarily would, only you preface your search term with a special operator. That operator ensures that results to your query are filtered accordingly, based on whichever operator you choose to use.

Let's see an example:

![](../../../../../.gitbook/assets/image%20%28137%29.png)

The following operators were used:

* `site:` bbc.co.uk 
* `intitle:` liverpool

The result of this search will return only results were the word `liverpool` is in the title of the page, and the page is from the website is `bbc.co.uk`. Let's see the results:

![Results of the Google Dork search](../../../../../.gitbook/assets/image%20%28142%29.png)

As you can see, we have our results as expected. 

So, as you can see, Google Dorking is merely the act of filtering the millions upon millions of resources Google has to offer to only display things we are **REALLY** interested in. This probably sounds a little underwhelming - after all, the other name for Google Dorking is Google Hacking. But remember, hacking literally means to use something in a way other than its intended use, and as it transpires, there are lots of powerful \(and funny... and malicious...\) ways to leverage the power of Google Dorks.

