# Starting with vi

Most often, you start `vi` to open a particular file. For example, to open a file called `/tmp/test`, enter the following command:

```
vi /tmp/test
```

If this is a new file, you should see something similar to the following:

![Opening /tmp/test in vi](<../../../../../../.gitbook/assets/image (78).png>)

A blinking box at the top represents where your cursor is located. The bottom line keeps you informed about what is going on with your editing (here, you just opened a new file). In between, there are funny looking characters known as tildes (`~`) - they act as filler because there is no text in the file yet.

Now here’s the intimidating part...

### **There are no hints, menus, or icons to tell you what to do**

To make things worse, you can’t just start typing. If you do, the computer is likely to beep at you (and some people complain that Linux isn’t friendly...). To understand what is happening here, you first need to know the two main operating contexts: **command** mode and **input** mode.

{% hint style="info" %}
The `vi` editor _**always starts in command mode**_.
{% endhint %}

Before you can add or change text in the file, you have to type a command (one or two letters, sometimes preceded by an optional number) to tell `vi` what you want to do.

{% hint style="info" %}
_**Case is important, so use uppercase and lowercase exactly as shown in the examples...**_
{% endhint %}
