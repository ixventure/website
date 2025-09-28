---
layout: default
title: Home
---

# Welcome to IxVenture, a Legal Technologies Studio
***We Believe in Legal Formalism as Software:***

*<ins>Bringing humanitarian peace & joy to the world with lawcare-abundance</ins>.*

---
---

## Our Projects

<div class="project-grid">
  {% for project in site.projects %}
    {% assign project_slug = project.slug | default: project.name | split: "." | first %}
    {% assign project_path = '/assets/projects/' | append: project_slug %}

    <div class="project-card">
      <a href="{{ project.url | relative_url }}">
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" -%}
        {%- assign numbered_files = "" | split: "" -%}

        {%- for f in project_files -%}
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

## Our Operations

<div class="project-grid">
  {% for op in site.operations %}
    {% assign op_slug = op.slug | default: op.name | split: "." | first %}
    {% assign op_path = '/assets/operations/' | append: op_slug %}

    <div class="project-card">
      <a href="{{ op.url | relative_url }}">
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign op_files = site.static_files | where_exp: "f", "f.path contains op_path" -%}
        {%- assign numbered_files = "" | split: "" -%}

        {%- for f in op_files -%}
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
               alt="{{ op.title }} thumbnail"
               loading="lazy">
        {% else %}
          <img class="project-thumb"
               src="{{ '/assets/images/logo.png' | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="IxVenture logo (fallback)"
               loading="lazy">
        {% endif %}

        <div class="project-title">{{ op.title }}</div>
        {% if op.description %}
          <div class="muted project-desc">{{ op.description }}</div>
        {% endif %}
      </a>
    </div>
  {% endfor %}
</div>

## Our Products

<div class="project-grid">
  {% for prod in site.products %}
    {% assign prod_slug = prod.slug | default: prod.name | split: "." | first %}
    {% assign prod_path = '/assets/products/' | append: prod_slug %}

    <div class="project-card">
      <a href="{{ prod.url | relative_url }}">
        {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
        {%- assign prod_files = site.static_files | where_exp: "f", "f.path contains prod_path" -%}
        {%- assign numbered_files = "" | split: "" -%}

        {%- for f in prod_files -%}
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
               alt="{{ prod.title }} thumbnail"
               loading="lazy">
        {% else %}
          <img class="project-thumb"
               src="{{ '/assets/images/logo.png' | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="IxVenture logo (fallback)"
               loading="lazy">
        {% endif %}

        <div class="project-title">{{ prod.title }}</div>
        {% if prod.description %}
          <div class="muted project-desc">{{ prod.description }}</div>
        {% endif %}
      </a>
    </div>
  {% endfor %}
</div>

{% include products.md %}

---
---

{% include about-us.md %}
