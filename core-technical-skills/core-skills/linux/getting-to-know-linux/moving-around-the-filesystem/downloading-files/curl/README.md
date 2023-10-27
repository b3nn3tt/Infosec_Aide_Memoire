# curl

`curl` is a command-line utility for transferring data from or to a server designed to work without user interaction. With `curl`, you can download or upload data using one of the supported protocols including HTTP, HTTPS, [SCP](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/) , [SFTP](https://linuxize.com/post/how-to-use-linux-sftp-command-to-transfer-files/) , and [FTP](https://linuxize.com/post/how-to-use-linux-ftp-command-to-transfer-files/) . `curl` provides a number of options allowing you to resume transfers, limit the bandwidth, proxy support, user authentication, and much more.

In this section, we will show you how to use the curl tool through practical examples and detailed explanations of the most common curl options.

### General Syntax

The syntax for the `curl` command is as follows:

```
curl [options] [URL...]
```

In its simplest form, when invoked without any option, `curl` displays the specified resource to the standard output (usually your Terminal Window). For example, to retrieve the `example.com` homepage you would run:

```
curl example.com
```

The command will print the source code of the `example.com` homepage in your terminal window:

![An example of curl in action](<../../../../../../../.gitbook/assets/image (38).png>)

{% hint style="info" %}
If no protocol is specified, `curl` tries to guess the protocol you want to use, and it will default to `HTTP`.
{% endhint %}

## Additional Options

`curl` is a very versatile tool, and as such it has an array of useful functionality. In this section, we will concentrate primarily on the download capabilities of `curl`, however, there is a section in the Penetration Testing section where some of the more advanced features of `curl` are explored.

### Outputting to a File

To save the result of the `curl` command, use either the `-o` or `-O` option.&#x20;

Lowercase `-o` saves the file with a predefined filename, which in the example below is `vue-v2.6.10.js`:

```
curl -o vue-v2.6.10.js https://cdn.jsdelivr.net/npm/vue/dist/vue.js
```

Uppercase `-O` saves the file with its original filename:

```
curl -O https://cdn.jsdelivr.net/npm/vue/dist/vue.js
```

####

### Resume a Download

You can resume a download by using the `-C -` option. This is useful if your connection drops during the download of a large file, and instead of starting the download from scratch, you can continue the previous one.

For example, if you are downloading the Ubuntu 18.04 iso file using the following command:

```
curl -O http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso
```

and suddenly your connection drops you can resume the download with:

```
curl -C - -O http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso
```

####

### Follow a HTTP Redirect

&#x20;By default, `curl` doesn’t follow the HTTP Location headers.  If you try to retrieve the non-www version of `google.com`, you will notice that instead of getting the source of the page you’ll be redirected to the www version:

![HTTP 301 redirect - curl merely displays the message and does not follow its instruction](<../../../../../../../.gitbook/assets/image (97).png>)

&#x20;The `-L` option instructs `curl` to follow any redirect until it reaches the final destination:

![The original HTTP 301 as above, followed by an example of following the redirect](<../../../../../../../.gitbook/assets/image (13).png>)

####

### Modify the User-Agent String

Sometimes when downloading a file, the remote server may be set to block the Curl User-Agent, or to return different contents depending on the visitor device and browser. In situations like this, to emulate a different browser you can use the `-A` option.

For example to emulates Firefox 60 you would use:

```
curl -A "Mozilla/5.0 (X11; Linux x86_64; rv:60.0) Gecko/20100101 Firefox/60.0" https://getfedora.org/
```

####

### Transfer Files via FTP

To access a protected FTP server with `curl`, use the `-u` option and specify the username and password as shown below:

```
curl -u FTP_USERNAME:FTP_PASSWORD ftp://ftp.example.com/
```

Once logged in, the command lists all files and directories in the user’s home directory. You can then download a single file from the FTP server using the following syntax:

```
curl -u FTP_USERNAME:FTP_PASSWORD ftp://ftp.example.com/file.tar.gz
```

&#x20;To upload a file to the FTP server, use the `-T` followed by the name of the file you want to upload:

```
curl -T newfile.tar.gz -u FTP_USERNAME:FTP_PASSWORD ftp://ftp.example.com/
```

####

### Using a Proxy

`curl` supports different types of proxies, including HTTP, HTTPS and SOCKS. To transfer data through a proxy server, use the `-x` (`--proxy`) option, followed by the proxy URL.

The following command downloads the specified resource using a proxy on `192.168.44.1` port `8888`:

```
curl -x 192.168.44.1:8888 http://linux.com/
```

If the proxy server requires authentication, use the `-U` (`--proxy-user`) option followed by the user name and password separated by a colon (`user:password`):

```
curl -U username:password -x 192.168.44.1:8888 http://linux.com/
```

####

### Send Cookies

Sometimes you may need to make an HTTP request with specific cookies to access a remote resource or to debug an issue. By default, when requesting a resource with `curl`, no cookies are sent or stored.

To send cookies to the server, use the `-b` switch followed by a filename containing the cookies or a string.

For example, to download the Oracle Java JDK rpm file `jdk-10.0.2_linux-x64_bin.rpm` you’ll need to pass a cookie named `oraclelicense` with value `a`:

```
curl -L -b "oraclelicense=a" -O http://download.oracle.com/otn-pub/java/jdk/10.0.2+
```





