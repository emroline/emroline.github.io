---
#subtitle: "Algorithms"
#author: anuroop
categories: [ Python, Python Examples]
#excerpt: 
tags: []
under_development: false
---

While writing our Python programs, many times we need to get input from user. Python makes it very easy for us to get user input.

Python3 provides an inbuilt function to read input from keyboard.

### input(prompt)

`input()` function in Python takes exactly what is typed from our keyboard and returns it as a string. We can store the returned string in a variable(a named location in system's memory) or use it right away without explicitly storing. 

Following is a sample code snippet to demonstrate how `input()` function can be used in our programs:

{% highlight python %}
{% raw %}
# Python program to demonstrate use of input() function

# Any string supplied as parameter of input() function will appear a hint in terminal.
user_input = input("Enter something")
print(user_input)
{% endraw %}
{% endhighlight %}

> **Note:** input() function in Python3 always returns a string. You  will have to convert the datatype in some use cases.

Following example shows how you can take integer input from user:

{% highlight python %}
{% raw %}
# Python program to demonstrate use of input() function
# and how to get integer input
# Any string supplied as parameter of input() function will appear before the prompt in terminal.
integer_user_input = input("Enter some integer")
integer_user_input = int(integer_user_input) # Converting string to integer

integer_user_input + 55 # You can't add an string to an integer
print(integer_user_input)

{% endraw %}
{% endhighlight %}

### How the input function works in Python?

* When the interpreter reaches the input() function, the program flow will be stopped until user has given an input.
* The programmer can supply some hint to the user by supplying some string in input() function, eg. `input("This is some hint")`
* Whatever you enter as input, the input() function will convert it to string. You will need to explicitly convert it into the appropriate datatype, using typecasting.

Example code to test input datatype:

{% highlight python %}
{% raw %}
# Program to check the input data type Python
var = input("Enter something...:")
print(var)

# Printing the type of input
print("Type of input stored in var variable", type(var))

{% endraw %}
{% endhighlight %}