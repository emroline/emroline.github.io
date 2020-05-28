---
title: "Papers"
permalink: /papers/
layout: single
date: false
---

<ul>
{% for post in site.posts %} 
    <li><a href="{{ post.url | relative_url }}" rel="permalink">{{ post.title }}</a></li>
{% endfor %}
</ul>