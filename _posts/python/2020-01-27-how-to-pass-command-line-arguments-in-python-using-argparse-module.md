---
title: "How To Pass Command Line Arguments In Python Using argparse Module"
categories: [ Python]
#excerpt: 
tags: []
under_development: false
---
Python provides an **argparse** module, which makes it easy to write user-friendly command-line interfaces. In a program you can define the required arguments, and `argparse` will figure out how to parse those arguments.

The `argparse` module also automatically generates help and usage messages and issue errors when users give the program invalid arguments.

Following is an example of how to use `argparse` module in your program to pass parameters as command line arguments:

{% highlight python %}
{% raw %}

import argparse
parser = argparse.ArgumentParser()
parser.add_argument("x", type=int, help="the base")
parser.add_argument("y", type=int, help="the exponent")
args = parser.parse_args()
answer = args.x**args.y
print("{} to the power {} equals {}".format(args.x, args.y, answer))

{% endraw %}
{% endhighlight %}

Some notes on above snippet:
* In  `import argparse` is used to import the `argparse` module in our script.
* We used `parser = argparse.ArgumentParser()` to initiate a new object named `parser` of type `argparse.ArgumentParser`.
* Then we add two arguments named `x` and `y` using `add_argument`.

Now run the script as follows:

{% highlight terminal %}
{% raw %}

python3 sys_argv.py 10 2
{% endraw %}
{% endhighlight %}

The output will be:
{% highlight terminal %}
{% raw %}

10 to the power 2 equals 100

{% endraw %}
{% endhighlight %}

The `argparse` module provides inbuilt support for `--help` argument, so if we execute the script like following:

{% highlight terminal %}
{% raw %}

python3 sys_argv.py --help
{% endraw %}
{% endhighlight %}

The output will be:
{% highlight terminal %}
{% raw %}

usage: sys_argv.py [-h] x y

positional arguments:
  x           the base
  y           the exponent

optional arguments:
  -h, --help  show this help message and exit

{% endraw %}
{% endhighlight %}