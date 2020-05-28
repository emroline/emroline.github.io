---
categories: [ Flutter, Dart]
#excerpt: 
tags: []
under_development: false
---
<p class="text-center">
<img src="/assets/images/dart-logo.png" alt="Dart Logo">
</p>
Dart is an open-source general-purpose programming language. Dart is an object oriented language. 

Following is a simple Dart program that prints some text:
{% highlight dart %}
{% raw %}
void main() {
    print("Hey, you are learning Dart!");
}
{% endraw %}
{% endhighlight %}

* Every Dart app has a main() function.
* print() is a top-level function in Dart, that can be used to print on console.

### Variables and Data types
Variable is a named storage location in the memory. Dart supports type inference. So even in type-safe Dart code, most variables don't need explicit types.

{% highlight dart %}
{% raw %}

void main() {
    // var keyword is used to declare a variable
    var name = "Voyager I"; //String
    var year = 1977; //Integer
    var antennaDiameter = 3.7; //Double
    var flybyObjects = ['Jupiter', 'Saturn', 'Uranus', 'Neptune']; //List
    var image = {
        'tags': ['saturn'],
        'url': '//path/to/saturn.jpg'
    };
    // final and const keywords are used to declare constants
    final a = 12; 
    const pi = 3.14;
}
{% endraw %}
{% endhighlight %}

Data types supported in Dart:
* Numbers - Use to represent numeric literals - Integer and Double
* Strings - Sequence of characters
* Booleans - used to represent a Boolean values - true and false
* Lists and Maps - Collection of objects.

**Note:** Dart does not support arrays. Dart collections can be used to replicate data structures such as arrays, generics, and optional typing.

### Control flow statements
{% highlight dart %}
{% raw %}

void main() {
    var mass = 23007

    if (mass >= 100000) {
        print("Planet is heavy");
    } else if (mass >= 200000) {
        print("Planet is very heavy");
    } else {
        print("Planet is not heavy");
    }

    var planets = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];

    for (var planet in planets) {
        print(planet);
    }

    for (int month = 1; month <=12; month++) {
        print(month);
    }

    var year = 2020;

    while (year < 2030) {
        year += 1;
        print(year);
    }
}
{% endraw %}
{% endhighlight %}

### Functions
{% highlight dart %}
{% raw %}
int fibonacci(int n) {
    if (n == 0 || n == 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

var result = fibonacci(20);
{% endraw %}
{% endhighlight %}

A shorthand => (arrow) syntax is handy for functions that contain a single statement. This syntax is especially useful when passing anonymous functions as arguments:

{% highlight dart %}
{% raw %}
flybyObjects.where((name) ==> name.containe('turn')).forEach(print);
{% endraw %}
{% endhighlight %}

In Dart a function can be used as an argument.

### Comments
{% highlight dart %}
{% raw %}
// This is a normal, one-line comment.

/// This is a documentation comment.
/// Tools like IDEs and dartdoc treat
/// doc comments specially.

/* Comments like these are also supported. */
{% endraw %}
{% endhighlight %}

### How to import
{% highlight dart %}
{% raw %}
// Importing core libraries
import 'dart:math';

// Importing libraries from external packages
import 'package:test/test.dart';

// Importing files
import 'path/to/my_other_file.dart';
{% endraw %}
{% endhighlight %}

### Object Oriented Programming
Dart is object-oriented language and supports object-oriented programming features like classes, interfaces, etc.

A class is a blueprint for creating objects.
{% highlight dart %}
{% raw %}
class Student {
    String name;

    //getter method
    String get student_name {
        return name;
    }

    //setter method
    String set student_name(String name) {
        this.name = name;
    }

    //function definition
    void result() {
        print(name);
    }
}

void main() {
    //creating object
    Student stud = new Student();
    stud.name = "student1";
    stud.result(); //function call
}
{% endraw %}
{% endhighlight %}
