---
#subtitle: "Algorithms"
#author: anuroop
categories: [ Python, Python Examples]
#excerpt: 
tags: []
under_development: false
---

In this example we will use Python to handle text files.
<!--end of excerpt-->

**Note:** In text files each line is terminated with a special character EOL (End Of Line). In Python EOL is represented as the new line character ("\n").

### File Access Modes
> "r" - Read. Raise I/O if file does not exist.  
> "r+" - Read and Write. Raise I/O if file does not exist.  
> "w" - Write. Creates file if it does not exist.  
> "w+" - Read and Write. Creates file if it does not exist.  
> "a" - Append. Creates file if it does not exist.  
> "a+" - Read and Append. Creates file if it does not exist.
> "x" - Create file. Raise error if file exists.

### Opening and Closing a file
We can open a file using `open()` function and close it using `close()` function.

>`File_object = open(r"File_Name","Access_Mode")`

If file is in same directory as the python program, we can simply use the filename, otherwise we will have to use the full path of that file in place of filename.

Following are some examples:
{% highlight python %}
{% raw %}
file1 = open("myfile.txt", "r")
file2 = open("/home/user/text_files/myfile.txt", "w")
file1.close()
file2.close()
{% endraw %}
{% endhighlight %}

### Reading an existing file
You can only read a file if it exists. To read a file we use `read()`, `readline()` and `readlines()`.

1. **read() :** Returns the file contents as string. Reads n bytes. If n is not specified, reads entire file.
`File_object.read([n])`
2. **readline() :** Reads one line and returns as string. Reads at most n bytes if n is given. Cannot return more than one line at a time.
`File_object.readline([n])`
3. **readlines() :** Reads whole content. Returns a list containing all the lines as elements.
`File_object.readlines()`

**Note:** ‘\n’ is treated as a special character of two bytes.

Following is an example:
{% highlight python %}
{% raw %}
f = open("myfile.txt", "r")
file_contents = f.read()
print(file_contents)

{% endraw %}
{% endhighlight %}


### Appending content to end of an existing file
To append content at the end of a file, we use `write()` and `writelines()` with access mode `"a"`.

Following is an example:
{% highlight python %}
{% raw %}

f = open("myfile.txt", "a")
f.write("This content will be added to the end of file.")
f.close()

{% endraw %}
{% endhighlight %}

### Overwriting the contents of a file
We use `write()` and `writelines()` with access mode `"w"`
{% highlight python %}
{% raw %}

f = open("myfile.txt", "w") # Will create new file if file does not exists
f.write("All previous contents will be overwritten by this content.")
f.close()

{% endraw %}
{% endhighlight %}
