---
title: My First Page
layout: default
---

This is the content of my page

{% include_relative abschnitt1.md %}

<ul>
  {% capture nowunix %}{{'now' | date: '%s'}}{% endcapture %}
  {% assign now_in_24h_unix = nowunix | plus: 86400 %}
  {% for post in site.posts reversed %}
    <li>
      {% capture posttime %}{{post.date | date: '%s' | plus: 0}}{% endcapture %}
      {% if posttime >= now_in_24h_unix %}
        <a href="{{ post.url }}">{{ post.date}} - {{ post.title }}</a>
      {% endif %}
    </li>
  {% endfor %}
</ul>
