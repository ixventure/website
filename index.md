---
layout: default
title: IxVentures
---

# IxVentures Studio
Welcome! Here’s what we’re working on:

<ul>
{% for project in site.projects %}
  <li>
    <a href="{{ project.url }}">{{ project.title }}</a> – {{ project.description }}
  </li>
{% endfor %}
</ul>
