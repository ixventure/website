---
layout: default
title: Projects
permalink: /projects/
---

# Projects

<div class="project-grid">
  {% for project in site.projects %}
    {% assign project_slug = project.slug | default: project.name | split: "." | first %}
    {% assign project_path = '/assets/projects/' | append: project_slug %}

    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {%- assign found_thumb = "" -%}
        {%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}
        {%- for f in project_files -%}
          {%- assign name = f.name | downcase -%}
          {%- if name contains "image-1." -%}
            {%- assign found_thumb = f.path -%}
            {%- break -%}
          {%- endif -%}
        {%- endfor -%}

        {% if found_thumb != "" %}
          <img class="project-thumb"
               src="{{ found_thumb | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="{{ project.title }} thumbnail"
               loading="lazy">
        {% else %}
          <img class="project-thumb"
               src="{{ '/assets/images/logo.png' | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="IxVenture logo"
               loading="lazy">
        {% endif %}

        <div class="project-title">{{ project.title }}</div>
        {% if project.description %}
          <div class="muted project-desc">{{ project.description }}</div>
        {% endif %}
      </a>
    </div>
  {% endfor %}
</div>
