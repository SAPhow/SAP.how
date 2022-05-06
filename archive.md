# Posts Archive

{%for post in site.posts %}
{% unless post.next %}
<ul class="this">
  {% else %}
  {% capture month %}{{ post.date | date: '%B %Y' }}{% endcapture %}
  {% capture nmonth %}{{ post.next.date | date: '%B %Y' }}{% endcapture %}
  {% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
  {% capture nyear %}{{ post.next.date | date: '%Y' }}{% endcapture %}
  {% if year != nyear %}
</ul>
<h3 style="text-align:left;">{{ post.date | date: '%Y' }}</h3>
<ul class="past">
  {% endif %}
  {% if month != nmonth %}
  <h4 style="text-align:left;">{{ post.date | date: '%B %Y' }}</h4>
  {% endif %}
  {% endunless %}
  <p><b><a href="{{ site.baseurl }}{{ post.url }}">{% if post.title and post.title != "" %}{{post.title}}{% else %}{{post.excerpt |strip_html}}{%endif%}</a></b> - {% if post.date and post.date != "" %}{{ post.date | date: "%e %B %Y" }}{%endif%}</p>
  {% endfor %}
</ul>
