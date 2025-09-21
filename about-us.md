---
layout: default
title: About Us
permalink: /about-us/
---

## What are We Obsessed With?

Continuing the inventor-class lawyer traditions of **juris doctor linguists** who have hyperdeflated legal costs worldwide:

* **Goldfarb**, the Internet's grandpa by inventing **Markup Language** _digital legal formalization_
  
* **Szabo**, the Blockchain's grandpa by inventing **Smart-Contract Language** _digital legal formalization_

Note that the Internet and the Blockchain are both legal expresions. They are a Commons of real-world relationships formalized through XML, Solidity, etc.

## Why are We Obsessed With It? 

The practice of law is hyperinflationary _and_ scarce nowadays: 

* But a world that enjoys legal abundance is **a humanitarian world filled with peace & joy**. (As we now enjoy with transport abundance compared to the scarcity of 200 years ago).
  
* Witnessing that many business opportunities do not begin only because legal costs are too high. This applies to many other prosocial chilling effects, many not normally capitalized so not well documented either.

* And perhaps digital legal formalism has mostly been expressed globally, not locally, so the balance between global disintermediation and local mediaries is off kilter.

## Our Sovtech Investment Category

Solutions touch on existing investment categories -- **AI**, **blockchain**, **legaltech** -- but the common **deeptech** category is sovtech: 

* **Sovtech** reinforces our rights to _sovereignty_ along the entire **individual -> multistate** vertical, because a break anywhere along the verticle can lead to catastrophy!

<div class="project-grid">
  {% for partner in site.about-us %}
    {% assign partner_slug = partner.slug | default: partner.name | split: "." | first %}
    {% assign partner_path = '/assets/about-us/' | append: partner_slug %}

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
