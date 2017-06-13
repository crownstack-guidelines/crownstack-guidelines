---
layout: post
title: Authors
skip_related: true
skip_footer: true
---

<div id="archive">
{% for author in site.data.authors %}
  <h2>{{ author }}</h2>
  {% for post in site.posts %}
    {% if author == post.author %}
    <li {% if post.favorite and post.layout != "writeup" %}class="favorite"{% endif %}>
      <a href="{{ post.url }}">{{ post.title }}{% if post.layout == "writeup" %} (Book Writeup){% endif %}</a>
    </li>
    {% endif %}
  {% endfor %}
{% endfor %}
</div>
