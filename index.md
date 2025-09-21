---
layout: default
title: Home
---

# Welcome to IxVenture
***Legal formalism** to change the world within the Goldfarb (Markup Language) and Szabo (Smart Contract) inventor-class lawyer tradition.*

## Why? 

Legal is hyperinflationary and scarce nowadays: 

* But a world that enjoys legal abundance is **a humanitarian world filled with peace & joy**. (As we now enjoy with transport abundance compared to the scarcity of 200 years ago).

## Sovtech

Solutions touch on existing investment categories -- **AI**, **blockchain**, **legaltech** -- but the common **deeptech** category is actually sovtech: 

* **Sovtech** reinforces our rights to sovereignty along the entire **individual -> multistate** vertical, because a break anywhere along the verticle can lead to catastrophy

## Our Projects

<div class="project-grid">
  {% for project in site.projects %}
    {% assign project_slug = project.slug | default: project.name | split: "." | first %}
    {% assign project_path = '/assets/projects/' | append: project_slug %}

    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {%- comment -%}
          Find the first image in the project folder (any name, robust, sorted by filename)
        {%- endcomment -%}
        {%- assign found_thumb = "" -%}
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}

        {%- for f in project_files -%}
          {%- assign ext = f.extname | remove: "." | downcase -%}
          {%- if extensions contains ext -%}
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
               alt="IxVenture logo (fallback)"
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
