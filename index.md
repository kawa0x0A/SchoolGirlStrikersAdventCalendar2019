---
layout: page
---
{% for post in site.posts limit :10 %}
  <h1>
    <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
  </h1>
  <br>
  {{ post.content }}
  <hr>
{% endfor %}
