# Articles

## Contents

- [Latest articles](#latest-articles)
- [SAP GUI](#sap-gui)
  - [Settings](#settings)
  - [Support](#support)
  - [Design](#design)
  - [Authorizations](#authorizations)
  - [Basis](#basis)
- [SAP EWM](#sap-ewm)
  - [Management](#management)
  - [Development](#development)
  
---
  
## Latest articles

{% for post in site.posts limit:3 %}
  — <small>{{ post.date | date: "%-d %B %Y" }}</small> —
  <h3>{{post.title}}</h3>
  {{ post.excerpt }}
  <a href="{{post.url}}">More about <cite>{{post.title}}</cite></a>
{% endfor %}

---

## SAP GUI

### Settings

{% for post in site.categories.gui-settings %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Support

{% for post in site.categories.gui-support %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Design

{% for post in site.categories.gui-design %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Authorizations

{% for post in site.categories.gui-authorizations %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Basis

{% for post in site.categories.gui-basis %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

---

## SAP EWM

### Management

{% for post in site.categories.ewm-management %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}

### Development

{% for post in site.categories.ewm-development %}
  - [{{ post.title }}]({{ post.url }})
{% endfor %}
