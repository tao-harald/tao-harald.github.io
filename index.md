---
layout: default
title: Home
cover: false
about: 'about.html'
---

<div class="vertical">
    <br />
    <div align="center">
        <h1>{{ site.title | default: site.github.repository_name }}</h1>
        {% if site.description %} <h4> {{site.description}} </h4> {% endif %}
        <h4>
            {% if page.about %} <a href='{{page.about | relative_url}}'> About me</a> {% endif %}
            &nbsp;
            <a href='gallery/'> Gallery </a>
        </h4>
        <br />
    </div>
{% for post in site.posts %}
  <h3>
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
</div>