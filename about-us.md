---
layout: default
title: About Us
permalink: /about-us/
---

# About Us

Welcome to IxVenture, a Legal Technologies Studio.  
We believe in **Legal Formalism as Software** and aim to bring humanitarian peace & joy to the world through lawcare-abundance.

---

## Our Story

IxVenture was founded to formalize legal and organizational logic in a programmable, transparent, and verifiable way. Our projects, partnerships, operations, and products embody this philosophy.

---

## Team Gallery

{% include gallery.html slug="about-us" title="About Us" folder="projects" %}

*Images above are ordered by number and display the first-numbered image as the thumbnail.*

---

## Team Resources

<div class="project-grid">
  {% assign folder = 'projects' %}
  {% assign about_files = site.static_files | where_exp: "f", "f.path contains '/assets/projects/about-us/'" | sort: "path" %}

  {% for f in about_files %}
    {% assign ext = f.extname | remove: "." | downcase %}
    {% if ext == "png" or ext == "jpg" or ext == "jpeg" or ext == "svg" %}
      <div class="project-card">
        <a href="{{ f.path | relative_url }}">
          <img class="project-thumb"
               src="{{ f.path | relative_url }}?v={{ site.time | date: '%s' }}"
               alt="About Us image"
               loading="lazy">
          <div class="project-title">{{ f.name | remove: f.extname }}</div>
        </a>
      </div>
    {% endif %}
  {% endfor %}
</div>
