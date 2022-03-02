# Passive Reconnaissance

As we have already acknowledged, Passive Reconnaissance centres around the requirement to gather as much information about our target as possible, whilst maintaining a "_zero touch_" approach. When we use the phrase zero touch, what we mean is that we will only examine sources of information that are considered public, and therefore interaction with them is entirely in keeping with their intended use case.

For example, let's assume that your target organisation has its own publicly accessible website. To simply browse the website would be considered zero touch, as you are interacting with the website in the intended way. However, let's imagine that halfway through your session, you spot a log on portal designed for authorised employees only. To try and gain unauthorised access at this point, possibly by brute force or some other method, involves interacting with the target - this would immediately fall under the realms of **Active** reconnaissance.

{% hint style="info" %}
Admittedly, the phrase **zero touch** is a little misleading, which is why fewer people use it today. However, it is still used actively in many security communities, so it is worth mentioning for completeness
{% endhint %}

Examples that are much more distinct in their passive nature are:

* Public DNS records\

* Search engine enumeration (Google, Bing, DuckDuckGo etc...)\

* Publicly offered Intellectual Property (GitHub repositories, PasteBin etc...)\

* Social Media (Twitter, FaceBook, LinkedIn etc...)\

* Job advertisements\

* and many more

Consider the above list. Your target organisation is highly unlikely to be notified every time one of its employees is looked at on LinkedIn. However, a lot of useful information can be gathered from a simple employee profile. For example, imagine you have found 3 employees who are all working in the IT department of your target, all of whom are certified in CISCO networks, and have Microsoft professional accreditations - it's highly likely you just worked out what tech stack the organisation is running.&#x20;

Now let's imagine that you find a job advert for the same company, this time hiring for a Security Analyst to work in their Operations Centre. The job spec has an exhaustive list of skills that are mandatory for the role, and suggests that familiarisation with tools like [Splunk](https://www.splunk.com) or [ELK](https://www.elastic.co/what-is/elk-stack) would be beneficial. This could be interesting for two reasons:

1. There is the suggestion that perhaps their ops team is running light, hence needing to hire people; does this decrease their likelihood of catching you red handed?\

2. We now have a better understanding of the level of skill expected of their analysts, and the tools they use to catch would be attackers. Does this help us to shape our approach?

Gaining this type of knowledge can help in many ways. For example, it could help you reduce the volume of traffic you ultimately end up sending to your target in the active reconnaissance and exploitation phases of the engagement. This could make the difference between success, and failure because you got caught firing too much traffic at your target, or because you underestimated their response capability.

When activities are constrained solely to publicly available information, then this type of research is referred to as Open Source Intelligence (OSINT) gathering. As per his [article](https://www.computerweekly.com/tip/Using-open-source-intelligence-software-for-cybersecurity-intelligence) written in Computer Weekly, [Michael W. McLaughlin](https://www.techtarget.com/contributor/Michael-W-McLaughlin?\_gl=1\*1vjbvkg\*\_ga\*MTM5ODg2OTgxMy4xNjMyOTE2NjA2\*\_ga\_TQKE4GS5P9\*MTYzMjkxNjYwNS4xLjAuMTYzMjkxNjYwNS4w&\_ga=2.50146852.300275541.1632916606-1398869813.1632916606) defines OSINT as:

> _a method of using open source tools to collect information from publicly available sources and then analyse it in order to make a decision or take some action. OSINT can be helpful in the right hands, but harmful when hackers use it to learn more about your organisation_

So, let's take a look at some techniques we can use.
