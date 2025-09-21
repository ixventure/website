---
layout: default
title: About
permalink: /about/
---

# about

<div class="project-grid">
  {% for partner in site.about %}
    {% assign partner_slug = partner.slug | default: partner.name | split: "." | first %}
    {% assign partner_path = '/assets/about/' | append: partner_slug %}

    <div class="project-card">
      <a href="{{ partner.url | relative_url }}">
        {%- assign found_thumb = "" -%}
        {%- assign partner_files = site.static_files | where_exp: "f", "f.path contains partner_path" | sort: "path" -%}

        {%- for f in partner_files -%}
          {%- assign name_no_ext = f.name | remove: f.extname | remove: "." | downcase -%}
          {%- assign parts = name_no_ext | split: "-" -%}
          {%- assign last_part = parts | last | plus: 0 -%}
          {%- if last_part > 0 -%}
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
