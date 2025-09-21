---
layout: default
title: Home
---

# Welcome to IxVenture
***Legal formalism as software** <ins>bringing humanitarian peace & joy to the world</ins>.*

Continuing the inventor-class lawyer traditions of **juris doctor linguists**: 

* **Goldfarb** is the Internet's grandpa because he invented **Markup Language** _digital legal formalization_
  
* **Szabo** is the Blockchain's grandpa because he invented **Smart-Contract Language** _digital legal formalization_

---

## Our Projects

<div class="project-grid">
  {% for project in site.projects %}
    {% assign project_slug = project.slug | default: project.name | split: "." | first %}
    {% assign project_path = '/assets/projects/' | append: project_slug %}

    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
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

## Our Partnerships

<div class="project-grid">
  {% for partner in site.partnerships %}
    {% assign partner_slug = partner.slug | default: partner.name | split: "." | first %}
    {% assign partner_path = '/assets/partnerships/' | append: partner_slug %}

    <div class="project-card">
      <a href="{{ partner.url | relative_url }}">
        {%- assign found_thumb = "" -%}
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign partner_files = site.static_files | where_exp: "f", "f.path contains partner_path" | sort: "path" -%}

        {%- for f in partner_files -%}
          {%- assign ext = f.extname | remove: "." | downcase -%}
          {%- if extensions contains ext -%}
            {%- assign found_thumb = f.path -%}
            {%- break -%}
          {%- endif -%}
        {%- endfor -%}

        {% if found_thumb != "" %}
          <img class="project-thumb"
               src="{{ found_thumb | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="{{ partner.title }} thumbnail"
               loading="lazy">
        {% else %}
          <img class="project-thumb"
               src="{{ '/assets/images/logo.png' | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="IxVenture logo (fallback)"
               loading="lazy">
        {% endif %}

        <div class="project-title">{{ partner.title }}</div>
        {% if partner.description %}
          <div class="muted project-desc">{{ partner.description }}</div>
        {% endif %}
      </a>
    </div>
  {% endfor %}
</div>

</br >

---

## Why? 

Legal is hyperinflationary and scarce nowadays: 

* But a world that enjoys legal abundance is **a humanitarian world filled with peace & joy**. (As we now enjoy with transport abundance compared to the scarcity of 200 years ago).

## Sovtech

Solutions touch on existing investment categories -- **AI**, **blockchain**, **legaltech** -- but the common **deeptech** category is sovtech: 

* **Sovtech** reinforces our rights to _sovereignty_ along the entire **individual -> multistate** vertical, because a break anywhere along the verticle can lead to catastrophy
