---
title: My First Page
layout: default
---

This is the content of my page

{% include_relative abschnitt1.md %}

<ul>
  {% capture now_unix %}{{'now' | date: '%s'}}{% endcapture %}
  {% assign now_in_24h_unix = now_unix | plus: 86400 %}
  {% assign count = 0 %}
  
  {% for post in site.posts reversed %}
  
    {% capture posttime %}{{post.date | date: '%s' }}{% endcapture %}
    {% assign posttime_unix = posttime | plus: 0 %}
    {% if posttime_unix >= now_in_24h_unix and count < 3 %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
      {% assign count = count | plus: 1 %}
    {% endif %}
  {% endfor %}
</ul>
