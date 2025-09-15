---
layout: home
title: IxVentures
---

# IxVentures Studio

Welcome! Here’s what we’re working on:

{% if site.projects and site.projects != empty %}
<ul class="post-list">
  {% for project in site.projects %}
    <li>
      <h2>
        <a href="{{ project.url | relative_url }}">
          {{ project.title }}
        </a>
      </h2>
      <p>{{ project.description }}</p>
    </li>
  {% endfor %}
</ul>
{% else %}
<p>No projects yet — stay tuned!</p>
{% endif %}
