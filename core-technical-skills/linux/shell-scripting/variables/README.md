# Variables

Think of a variable as a named bucket that we can place data into. We can then use these variables (or, more practically, their contents) within our code.

To create, or “Declare” a variable, simply enter its name followed by an `=` with no spaces, and then the value of the variable (again with no spaces):

{% code title="Declaring Variables" %}
```bash
example_variable=Good
example_variable2=Bad
```
{% endcode %}

{% hint style="info" %}
Pro-Tip: **BE CONSISTENT WITH YOUR NAMING SCHEMA**
{% endhint %}

We can then reference variables with a $ sign:

{% code title="Calling Variables" %}
```bash
echo $example_variable $example_variable2
Good Bad
```
{% endcode %}

Now, there are a few tripping points here. Look at the following:

```bash
example=Hello World
bash: World: command not found
```

Because there was a space in the variable value, bash tried to interpret it, viewing World as a command. To get around this, we have to encapsulate our input in either `' '` or `" "`, but there are differences between them...

* `‘ ’` - The contents between them are literal, including special characters
* `“ ”` - The contents between them are literal, but certain special characters are still interpreted, such as `$`, `\`, and `` ` ``

{% code title="Examples of Encapsulation" %}
```bash
greeting='Hello World'
echo $greeting
Hello World

greeting2="New $greeting"
echo $greeting2
New Hello World
```
{% endcode %}
