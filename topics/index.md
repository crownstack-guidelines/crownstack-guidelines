---
layout: post
title: Topics
skip_related: true
skip_footer: true
---

<div id="archive">
  {% for series in site.data.series %}
    <h3 id="{{ series.tag_name }}">{{ series.name }}</h3>

    <ul>
      {% for post in site.tags[series.tag_name] %}
      <li {% if post.favorite and post.layout != "writeup" %}class="favorite"{% endif %}>
        <a href="{{ post.url }}">{{ post.title }}{% if post.layout == "writeup" %} (Book Writeup){% endif %}</a>
      </li>
      {% endfor %}
    </ul>
  {% endfor %}


  <h3 id="writeup">Books</h3>
  <ul>
    {% for post in site.categories.writeup %}
      <li {% if post.favorite %}class="favorite"{% endif %}>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
    {% endfor %}
  </ul>

</div>
