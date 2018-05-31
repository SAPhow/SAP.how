---
title: SAP.how
description: "Search SAP.how"
permalink: /
tipue_search_active: true
---

# Welcome to SAP.how

- [SAP EWM](http://sap.how/ewm)
- [Articles](http://sap.how/articles)

---

# Latest articles

{% for post in site.posts limit:5 %}
  — <small>{{ post.date | date: "%-d %B %Y" }}</small> —
  <h3>{{post.title}}</h3>
  {{ post.excerpt }}
  <a href="{{post.url}}">More about <cite>{{post.title}}</cite></a>
{% endfor %}
