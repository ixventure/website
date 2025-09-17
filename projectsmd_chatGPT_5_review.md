# Line-by-Line Review of `projects.md`

**Commit reviewed:** `99d55b962ed23430082934f74030d92048274735`

---

## 1. Front Matter

```yaml
---
layout: default
title: Projects
permalink: /projects/
---
```
- `layout: default` — Uses the site default layout for consistent framing.  
- `permalink: /projects/` — Ensures the projects listing lives at `/projects/` regardless of collection settings.

---

## 2. Purpose & Structure

- The file builds an index/grid of all `site.projects` (your `projects` collection).  
- For each project it tries to resolve a thumbnail by searching `site.static_files` for files inside `/assets/projects/<slug>/` whose name contains `image-1.`. If found, that image becomes the project's thumbnail; otherwise a fallback logo is used.

Key Liquid logic (paraphrased):

```liquid
{%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}
{%- for f in project_files -%}
  {%- assign name = f.name | downcase -%}
  {%- if name contains "image-1." -%}
    {%- assign found_thumb = f.path -%}
    {%- break -%}
  {%- endif -%}
{%- endfor -%}
```

---

## 3. Rendering Notes & Edge Cases

- `site.static_files` includes all files under `assets/` (because `_config.yml` includes `assets`). Ensure no unexpected files collide with the project path matching logic. If you have filenames that contain the substring used in `project_path`, they may be (incorrectly) included.
- Sorting by `path` helps pick a deterministic file, but naming convention (`image-1.*, image-2.*`) is the real contract here.
- `project.url | relative_url` is used to link to each project page — ensure each project file has proper `slug` or `permalink` so the link generates correctly.

---

## 4. Suggestions

- Consider adding an explicit `thumbnail` front-matter field to project files to simplify logic and avoid scanning `site.static_files` at build-time.
- If performance is a concern for very large `assets/`, pre-building a small `projects.json` or using `jekyll-assets` might speed up builds.
- Keep naming consistent: `image-1.png` as the preferred thumbnail filename for each project directory.

---

**Reviewed for educational literacy by ChatGPT‑5.**
