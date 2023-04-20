---
title: My First Page
layout: default
---

<div class="homepage-slider slider slider-3">
<ul>
  {% capture now_unix %}{{'now' | date: '%s'}}{% endcapture %}
  {% assign now_in_24h_unix = now_unix | plus: 86400 %}
  {% assign count = 0 %}
  
  {% for post in site.posts reversed %}
  
    {% capture posttime %}{{post.date | date: '%s' }}{% endcapture %}
    {% assign posttime_unix = posttime | plus: 0 %}
    {% if posttime_unix >= now_in_24h_unix and count < 3 %}
      <li style="background-image: url('img/slider-1.jpg')">
        <aside>
          <small>demnächst</small>
          <h1>{{ post.title }}</h1>
          <a class="linkbutton" href="{{ post.url }}">mehr</a>
        </aside>
      </li>
      {% assign count = count | plus: 1 %}
    {% endif %}
  {% endfor %}
</ul>
<a id="weiter" class="linkbutton" href="#angebote">&#x2B07;</a>
</div>

        <a name="angebote" id="angebote"></a>
{% include_relative abschnitt1.md %}

