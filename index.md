---
layout: home
title: IxVentures
---

# IxVentures Studio

Welcome! Here’s what we’re working on:

{% if site.projects and site.projects != empty %}
<div class="projects-grid">
  {% for project in site.projects %}
    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {% if project.thumbnail %}
          <img src="{{ project.thumbnail | relative_url }}" alt="{{ project.title }} thumbnail" class="project-thumb">
        {% endif %}
        <h2>{{ project.title }}</h2>
        <p>{{ project.description }}</p>
      </a>
    </div>
  {% endfor %}
</div>
{% else %}
<p>No projects yet — stay tuned!</p>
{% endif %}
