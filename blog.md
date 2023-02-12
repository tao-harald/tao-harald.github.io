---
layout: default
title: About me
---

{% for post in site.posts %}
  <h3 align="middle">
    <a href="{{ post.url }}">{{ post.title }}</a>
  </h3>
  <p>
    {% if post.abstract %}
      {{ post.abstract }}
    {% else %}
      {{ post.excerpt }}
    {% endif %}
  </p>
  <br />
{% endfor %}
<br />