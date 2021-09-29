# FOCA

Fingerprinting Organizations with Collected Archives \(FOCA\) is a tool used mainly to **find metadata and hidden information in the documents it scans**. These documents may be on web pages, and can be downloaded and analysed with FOCA.

It is capable of analysing a wide variety of documents, with the most common being **Microsoft Office**, **Open Office**, or **PDF** files, although it also analyses Adobe InDesign or SVG files, for instance.

These documents are searched for using three possible search engines: Google, Bing, and DuckDuckGo. The sum of the results from the three engines amounts to a lot of documents. It is also possible to add local files to extract the EXIF information from graphic files, and a complete analysis of the information discovered through the URL is conducted even before downloading the file.



## Using FOCA

The process works as follows:

Click on “New Project” on the top left hand Window. Fill in the “Domain Website” as our target, and name the project accordingly. Once all data has been entered, click "Create":

![](../../../.gitbook/assets/image%20%28130%29.png)

![](../../../.gitbook/assets/image%20%28122%29.png)

Next, on the new project screen, we can select which search engines to leverage \(Google, Bing etc.\) and what extensions to look for. Select those you wish to search \(leave default for maximum capture\):

![](../../../.gitbook/assets/image%20%28139%29.png)

Click “Search All”. The scan takes some time. Once complete, you can browse the discovered files. Right click the discovered files and select “Download All”:

![](../../../.gitbook/assets/image%20%28102%29.png)

Once all discovered files are downloaded, right click any of them and select "Extract All Metadata". You will now see the available data in the left side bar:

![](../../../.gitbook/assets/image%20%2895%29.png)

With the metadata now extracted, we can now right click and select “Analyse metadata”. This will give us information on the machine used to create that specific file.

FOCA features other scan options that should be explored. To do this:

1. Click on the “Network” section of the left side pane 
2. In the network window, you can select a variety of options, such as the search engine to be used, DNS options \(including zone transfer attempt\). There is also the ability to specify a brute force word list. Next, we can leverage the Bing IP search ability. Finally, we can select if we want to perform a reverse lookup via a PTR scan. Note that this takes a LONG TIME... 
3. Simply click start to launch the scan. Any discovered information will automatically populate the left side pane, just as before

















