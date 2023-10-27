# axel

Meet `axel` – it's like a turbo booster for your downloads. Instead of just one connection, it uses several at once to pull files from FTP or HTTP servers, making things much faster. While it's got a bunch of cool tricks up its sleeve, a favorite is `-n`, where you tell it how many connections to use.&#x20;

Check out this example: We're using `-a` for a neat and tidy progress bar and `-o` to give our downloaded file a fresh new name.

```
axel -a -n 20 -o report_axel.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf
```

![axel running a download, leveraging 20 connections](<../../../../../../.gitbook/assets/image (127).png>)

{% hint style="info" %}
For those playing close attention, yep, that URL is a sample pen-testing report from the folks at Offensive Security, or [OffSec](https://www.offsec.com/) as they're now called. Fun fact: I stumbled upon this tool while grinding through my [OSCP](https://www.offsec.com/courses/pen-200/) a couple years back.&#x20;

Shoutout to OffSec for the awesome tip!
{% endhint %}
