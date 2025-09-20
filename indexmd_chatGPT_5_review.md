# `index.md` Explanation

---

## Front Matter

```yaml
---
layout: default
title: Home
---
```

- **layout**: Uses the `default` layout for site-wide structure (header, footer, navigation).  
- **title**: Sets the page title to `Home`, which appears in the browser tab and metadata.  

---

## Page Content

```markdown
# Welcome to IxVenture
Building something amazing with AI.
```

- **H1 Heading**: Introduces the site with a clear message.  
- **Paragraph**: Brief tagline (“Building something amazing with AI.”).  

This creates a strong opening for visitors.

---

## Projects Section

```markdown
## Our Projects
```

- **H2 Heading**: Defines a section to list projects.  

---

## Project Grid Container

```html
<div class="project-grid">
  {% for project in site.projects %}
    ...
  {% endfor %}
</div>
```

- **Wrapper `<div>`**: Uses CSS class `project-grid` to display projects in a structured layout (likely CSS grid or flexbox).  
- **Loop**: Iterates through `site.projects` collection (defined in `_config.yml` or `_projects` folder).  

---

## Slug and Path Assignment

```liquid
{% assign project_slug = project.slug | default: project.name | split: "." | first %}
{% assign project_path = '/assets/projects/' | append: project_slug %}
```

- **Slug**: Chooses identifier from `project.slug`, falls back to `project.name`, removes extensions.  
- **Path**: Constructs path to project assets folder.  

---

## Project Card Wrapper

```html
<div class="project-card">
  <a href="{{ project.url | relative_url }}">
```

- **Card `<div>`**: Holds thumbnail, title, description.  
- **Anchor `<a>`**: Links project card to its detail page (`project.url`).  

---

## Thumbnail Selection Logic

```liquid
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
```

- **Initialize `found_thumb`**: Empty until match found.  
- **Allowed extensions**: Common image formats.  
- **File scan**: Collects static files in project path.  
- **Loop**: Finds first file with a valid extension, assigns as thumbnail, breaks loop.  

---

## Fallback Thumbnail

```liquid
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
```

- **Primary**: Displays first valid image found.  
- **Fallback**: Uses site logo if no images exist.  
- **Cache-busting**: Appends build timestamp query param.  
- **Accessibility**: Provides `alt` text.  
- **Performance**: Adds `loading="lazy"`.  

---

## Project Metadata

```liquid
<div class="project-title">{{ project.title }}</div>
{% if project.description %}
  <div class="muted project-desc">{{ project.description }}</div>
{% endif %}
```

- **Title**: Displays project’s title.  
- **Description (optional)**: Shows muted text if `project.description` is available.  

---

## Critique

1. **Strengths**
   - Dynamic and scalable: Loops over all projects automatically.  
   - Robust thumbnail logic: Works even if filenames differ, falls back gracefully.  
   - Accessibility-conscious: Includes alt text and lazy loading.  
   - Clear separation of structure (grid, cards) and data (projects).  

2. **Weaknesses**
   - Performance: Scanning all static files per project may slow builds for large repos.  
   - Cache-busting: Uses build time (`site.time`) instead of file modification/hash, so assets may not update reliably across builds.  
   - Accessibility: `alt` text defaults to generic “thumbnail” instead of descriptive labels.  
   - Design: Fallback logo may look repetitive if many projects lack images.  

3. **Suggestions for Improvement**
   - Use `_data` or front matter to specify thumbnail explicitly, avoiding file scans.  
   - Switch cache-busting to use file modification time or digest.  
   - Enhance `alt` text with project-specific descriptions for accessibility.  
   - Provide more distinctive fallback per project (e.g., generated initials or colors).  

---

✅ **Summary**:  
The `index.md` file serves as the home page, introducing the site and dynamically listing projects with thumbnails, titles, and optional descriptions. It balances robustness and usability but could be optimized for performance, accessibility, and design variety.
