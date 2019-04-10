---
layout: default
---

# About Me

I'm a master's student at Johns Hopkins with research interests in computer vision and machine learning with medical applications. I'm currently working with [Ayushi Sinha](https://www.cs.jhu.edu/~ayushis/).

# Projects

# Posts
<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{ post.url }}">
            {{ post.title }}
            </a>
            - <time datetime="{{ post.date | date: "%Y-%m-%d" }}">{{ post.date | date_to_long_string }}</time>
        </li>
    {% endfor %}
</ul>
