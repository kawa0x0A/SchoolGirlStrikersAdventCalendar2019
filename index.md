---
layout: default
---
{% for post in site.posts limit :10 %}
  <h1>
    <a href="{{ url }}{{ baseurl }}{{ post.url }}">{{ post.title }}</a>
  </h1>
  <br>
  {{ post.content }}
  <hr>
{% endfor %}
