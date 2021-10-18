---
layout: default
title: Home
cover: false
about: 'about.html'
---

<div class="vertical">
    <div align="center">
        <div style="font-size:4em">\(\tau_{\alpha o} \)</div>
        {% if site.description %} <h4> {{site.description}} </h4> {% endif %}
        <h4>
            {% if page.about %} <a href='{{page.about | relative_url}}'> About me</a> {% endif %}
            &nbsp;
            <a href='gallery/'> Gallery </a>
        </h4>
        <br />
    </div>
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
</div>