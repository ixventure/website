---
layout: home
title: IxVenture
---

# IxVenture Studio

Welcome! Here’s what we’re working on:

{% if site.projects and site.projects != empty %}
<div class="projects-grid">
  {% for project in site.projects %}
    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {% assign thumb = project.thumbnail %}

        {% if thumb == nil and project.images_path %}
          {% assign first_img = site.static_files 
            | where_exp:"file","file.path contains project.images_path" 
            | where_exp:"file","file.extname == '.png' or file.extname == '.jpg' or file.extname == '.jpeg' or file.extname == '.svg'" 
            | first %}
          {% if first_img %}
            {% assign thumb = first_img.path %}
          {% endif %}
        {% endif %}

        {% if thumb %}
          <img src="{{ thumb | relative_url }}" alt="{{ project.title }} thumbnail" class="project-thumb">
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
