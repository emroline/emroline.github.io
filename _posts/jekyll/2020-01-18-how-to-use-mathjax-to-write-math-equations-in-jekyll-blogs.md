---
#subtitle: "Math in Jekyll"
#author: anuroop
categories: [ Miscellaneous, Jekyll] 
excerpt: "MathJax can be used to render beautiful mathematics equations in a webpage. Using MathJax with Jekyll you can add math formulas to your blog page."
tags: [featured, Jekyll, Mathjax]
use_math: true
under_development: false
---
Create **mathjax_support.html** file in **_includes** directory. Add the following code to it:
{% highlight javascript %}
{% raw %}
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['$','$'], ['\(', '\)'] ],
      displayMath: [ ['$$','$$'] ],
      processEscapes: true,
    }
  });
</script>
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
{% raw %}
{% endhighlight %}

Open **_includes/head/custom.html** and add the code as shown below:
{% highlight javascript %}
{% raw %}
<!-- start custom head snippets -->
{% if page.use_math %}
    {% include mathjax_support.html %}
{% endif %}
<!-- end custom head snippets -->
{% endraw %}
{% endhighlight %}

If your projects structure is different from the default structure, then place the above snippet somewhere so that it is available to every page.

If the posts front-matter contains **use_math : true** MathJax support will be added to your post.

{% highlight yaml %}
layout: single
use_math: true
{% endhighlight %}

## Example

Now add the following MathJax code in your post:
{% highlight javascript %}
{% raw %}
$$ E = mc^2 $$
{% endraw %}
{% endhighlight %}
It will appear like this in the browser:  
$$ E = mc^2 $$