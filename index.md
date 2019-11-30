---
layout: default
---
{% for post in site.posts limit :10 %}
  <h1>
    <a href="{{ post.url }}">{{ post.title }}</a>
  </h1>
{% endfor %}
