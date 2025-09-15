---
layout: default
title: Projects
permalink: /projects/
---

# Projects

Here are the projects we’re working on:

<ul>
{% for project in site.projects %}
  <li>
    <a href="{{ project.url | relative_url }}">{{ project.title }}</a> — {{ project.description }}
  </li>
{% endfor %}
</ul>
