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
    {% capture posttime %}{{post.date | date: '%s' }}{% endcapture %}
    {% assign posttime_unix = posttime | plus: 0 %}
    {% if posttime_unix >= now_in_24h_unix %}
      <li>
        <a href="{{ post.url }}">{{ post.title }}</a>
      </li>
    {% endif %}
  {% endfor %}
</ul>
