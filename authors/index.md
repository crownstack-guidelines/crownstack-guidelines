---
layout: post
title: Authors
skip_related: true
skip_footer: true
---

<div id="archive">
{% for author in site.data.authors %}
<h2>{{ author[1].name }}</h2>
<ul>
{% for post in site.posts %}
{% if post.author == author[1].name %}
  <li {% if post.favorite and post.layout != "writeup" %}class="favorite"{% endif %}>
    <a href="{{ post.url }}">{{ post.title }}{% if post.layout == "writeup" %} (Book Writeup){% endif %}</a>
  </li>
  {% endif %}
{% endfor %}
</ul>
{% endfor %}
</div>
