# Line-by-Line Review of `index.md`

**Commit reviewed:** `d99ebf59ed973558b91d939c7f00f6765d0dea28`

---

## 1. Front Matter

```yaml
---
layout: default
title: Home
---
```
- `layout: default` — This page uses your site's default layout (found at `_layouts/default.html`) rather than a `home` layout. Good: keeps templates minimal and consistent.
- `title: Home` — Page title that can be used by the layout and for SEO.

---

## 2. Body Content & Project Grid

The body contains a `# Welcome to IxVenture` heading and a project grid that iterates `site.projects`. Key parts:

- The projects grid uses Liquid to iterate over `site.projects` and attempts to determine a thumbnail from `assets/projects/<slug>/image-1.*`. If found, it uses that image; otherwise falls back to `assets/images/logo.png` as a placeholder.
- Thumbs use `?v={{ site.time | date: '%s' }}` query param to force cache-busting on each build — this is a simple cache-busting approach to ensure changes deploy immediately.
- The loop also prints `project.title` and `project.description` when available.

Important lines (paraphrased):

```liquid
{% for project in site.projects %}
  {% assign project_slug = project.slug | default: project.name | split: "." | first %}
  {% assign project_path = '/assets/projects/' | append: project_slug %}
  {%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}
  {%- for f in project_files -%}
    {%- if f.name contains "image-1." -%} ... {% endif -%}
  {%- endfor -%}
{% endfor %}
```

---

## 3. Integration Notes & Suggestions

- Since `layout: default` is used, ensure `_layouts/default.html` includes any hero/title markup you expect (it likely already does).
- Consider using explicit `permalink` or consistent `slug` metadata in project files to avoid reliance on `project.name` parsing.
- Cache-busting with `site.time` forces clients to re-download images on every build — that's good for development, but in production it can prevent effective CDN caching. If you want long-lived caching for static assets, use file-hash or filename-versioning instead (and control cache headers via `_headers` which you already have).
- The Liquid used to find thumbnails is slightly complex but flexible; keep images named consistently (`image-1.png`) to ensure the first image is used as the thumbnail.

---

**Reviewed for educational literacy by ChatGPT‑5.**
