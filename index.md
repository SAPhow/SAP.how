---
title: SAP.how
description: "Search SAP.how"
layout: default
permalink: /
tipue_search_active: true
---

# Welcome to SAP.how

## Search

<form action="{{ page.url | relative_url }}">
  <div class="tipue_search_left"><img src="{{ "/assets/tipuesearch/search.png" | relative_url }}" class="tipue_search_icon"></div>
  <div class="tipue_search_right"><input type="text" name="q" id="tipue_search_input" pattern=".{3,}" title="At least 3 characters" required></div>
  <div style="clear: both;"></div>
</form>

<div id="tipue_search_content"></div>

<script>
$(document).ready(function() {
  $('#tipue_search_input').tipuesearch();
});
</script>

---
---

# Latest articles

{% for post in site.posts limit:10 %}
  — <small>{{ post.date | date: "%-d %B %Y" }}</small> —
  <h3>{{post.title}}</h3>
  {{ post.excerpt }}
  <a href="{{post.url}}">More about <cite>{{post.title}}</cite></a>
{% endfor %}
