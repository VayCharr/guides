---
layout: default
title: Vay's GitHub Pages
permalink: /
---

# Guides

<ul>
  {% assign guides = site.guides %}
  {% for guide in guides %}
    <li>
      <a href="{{ guide.url }}">{{ guide.title }}</a>
      <p>{{ guide.description | markdownify | strip_html | truncatewords: 20 }}</p>
    </li>
  {% endfor %}
</ul>
