# axel

[axel](https://github.com/axel-download-accelerator/axel) is a download accelerator that transfers a file from an FTP or HTTP server through multiple simultaneous connections. This tool has a vast array of features, but the most common is `-n`, which is used to specify the number of multiple connections to use.

In the following example, we are also using the `-a` option for a more concise progress indicator, and `-o` to specify a different file name for the downloaded file:

```text
axel -a -n 20 -o report_axel.pdf https://www.offensive-security.com/reports/penetration-testing-sample-report-2013.pdf
```

![axel running a download, leveraging 20 connections](../../../../../.gitbook/assets/image%20%2827%29.png)

## 

