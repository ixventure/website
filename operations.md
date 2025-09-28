---
layout: default
title: Operations
permalink: /operations/
---

# Operations

<div class="project-grid">
  {% for partner in site.operations %}
    {% assign partner_slug = partner.slug | default: partner.name | split: "." | first %}
    {% assign partner_path = '/assets/operations/' | append: partner_slug %}

    <div class="project-card">
      <a href="{{ partner.url | relative_url }}">
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign partner_files = site.static_files | where_exp: "f", "f.path contains partner_path" -%}
        {%- assign numbered_files = "" | split: "" -%}

        {%- for f in partner_files -%}
          {%- assign ext = f.extname | remove: "." | downcase -%}
          {%- if extensions contains ext -%}
            {%- assign name_no_ext = f.name | remove: f.extname | remove: "." -%}
            {%- assign parts = name_no_ext | split: "-" -%}

            {%- assign number_val = 0 -%}
            {%- for p in parts reversed -%}
              {%- assign try_num = p | plus: 0 -%}
              {%- if try_num > 0 -%}
                {%- assign number_val = try_num -%}
                {%- break -%}
              {%- endif -%}
            {%- endfor -%}

            {%- if number_val > 0 -%}
              {%- assign padded = number_val | plus: 100000 -%}
              {%- assign padded_str = padded | slice: 1,5 -%}
              {%- assign item = padded_str | append: "|" | append: f.path -%}
              {%- assign numbered_files = numbered_files | push: item -%}
            {%- endif -%}
          {%- endif -%}
        {%- endfor -%}

        {%- assign sorted_files = numbered_files | sort_natural -%}
        {%- if sorted_files.size > 0 -%}
          {%- assign first_file_parts = sorted_files | first | split: "|" -%}
          {%- assign found_thumb = first_file_parts[1] -%}
        {%- else -%}
          {%- assign found_thumb = "" -%}
        {%- endif -%}

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
