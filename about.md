---
title: My First Page
layout: default
---

This is the content of my page

{% include_relative abschnitt1.md %}

<ul>
  {% capture nowunix %}{{'now' | date: '%s'}}{% endcapture %}
  {% for post in site.posts reversed %}
    <li>
      {% capture posttime %}{{post.date | date: '%s'}}{% endcapture %}
      {% if posttime >= nowunix %}
        <a href="{{ post.url }}">{{ post.date}} - {{ post.title }}</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>
