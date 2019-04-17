---
layout: default
---

# Blog Posts

{% for category in site.categories %}
<h3>{{ category[0] }}</h3>
<ul>
{% for post in category[1] reversed %}
<li>
  <a href="{{ post.url }}">{{ post.title }}</a><br>
  {{ post.excerpt }}
</li>
{% endfor %}
</ul>
{% endfor %}