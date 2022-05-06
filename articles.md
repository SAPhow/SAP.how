---
title: Articles
permalink: /articles
---

<h1>Articles</h1>

<h2>List of contents</h2>

* This will become a table of contents (this text will be scrapped).
{:toc}

---
  
## Latest articles

{% for post in site.posts limit:3 %}
  — <small>{{ post.date | date: "%-d %B %Y" }}</small> —
  <h3>{{post.title}}</h3>
  {{ post.excerpt }}
  <a href="{{post.url}}">More about <cite>{{post.title}}</cite></a>
{% endfor %}

---

## Categories

{% capture categories %}
  {% for category in site.categories %}
    {% capture category_name %}{{ category | first }}{% endcapture %}
    |{{ category_name }}#
<ul>
    {% for post in site.categories[category_name] %}
<li><a href="{{post.url}}">{{post.title}}</a></li>
    {% endfor %}
</ul>
  {% endfor %}
{% endcapture %}
{% assign sortedcategories = categories | split: '|' | sort %}

{% for item in sortedcategories offset:1 %}
{% assign categoryitems = item | split: '#' %}
### {{ categoryitems[0] | upcase }}
{{ categoryitems[1] }}
{% endfor %}
