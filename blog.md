---
layout: post
title: The Real Magic of Bridge Foundry
---
{% for post in site.tags.ready %}

## [{{ post.title }} ]({{ site.github.url }}{{ post.url }})
{{ post.date | date_to_string }}
  {{ post.excerpt }}
[read more]({{ site.github.url}}{{ post.url }})
{% endfor %}
