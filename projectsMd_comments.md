# Line-by-Line Critique of `projects.md`

This file provides a line-by-line review of the `projects.md` file in the Jekyll repo, modeled after the style of the example at [myfmv.ai/prompts/13](https://myfmv.ai/prompts/13).

---

## Lines 1‑5: Front Matter

```liquid
---
layout: default
title: Projects
permalink: /projects/
---
```

**What it does:**  
Declares YAML front matter used by Jekyll, setting the layout to “default,” title to “Projects,” and permalink to `/projects/`.

**Strengths:**  
- Clear and minimal front matter.  
- Clean permalink, good for SEO.  
- Uses a layout for consistent styling.

**Potential Issues / Risks:**  
- Missing description/metadata for SEO and previews.

**Suggestions:**  
- Add optional metadata like `description:` or `image:` for social preview.

---

## Line 6: Main Heading

```markdown
# Projects
```

**What it does:**  
Renders a page heading.

**Strengths:**  
- Simple, clear.

**Weaknesses:**  
- Lacks context or intro text.

**Suggestions:**  
- Add a short intro sentence describing the projects.

---

## Lines 7‑35: Project Grid & Loop

```liquid
<div class="project-grid">
  {% for project in site.projects %}
    {% assign project_slug = project.slug | default: project.name | split: "." | first %}
    {% assign project_path = '/assets/projects/' | append: project_slug %}
    ...
  {% endfor %}
</div>
```

### Loop & Slug Assignment

**What it does:**  
- Iterates over `site.projects`.  
- Assigns a slug, falling back to project name.  
- Builds `project_path`.

**Strengths:**  
- Flexible fallback logic.  
- Standardized asset path.

**Weaknesses:**  
- Splitting by `.` may remove too much.  
- Slug may not be URL‑safe.

**Suggestions:**  
- Use `slugify`.  
- Document slug/asset folder conventions.

---

### Thumbnail Lookup Logic

```liquid
{%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}
...
{%- if last_part > 0 -%}
  {%- assign found_thumb = f.path -%}
  {%- break -%}
{%- endif -%}
```

**What it does:**  
- Scans static files in the project folder.  
- Chooses first file with numeric suffix (e.g. `-1.png`).

**Strengths:**  
- Automates thumbnail discovery.

**Weaknesses:**  
- Fragile naming assumption.  
- Build may slow with many files.

**Suggestions:**  
- Define `thumbnail:` in project front matter.  
- Or enforce strict naming convention.

---

### Rendering Thumbnail / Fallback

```liquid
{% if found_thumb != "" %}
  <img ... src="{{ found_thumb | relative_url }}?v={{ site.time | date: '%s' }}">
{% else %}
  <img ... src="{{ '/assets/images/logo.png' | relative_url }}?v={{ site.time | date: '%s' }}">
{% endif %}
```

**Strengths:**  
- Fallback prevents broken images.  
- Lazy loading is good.  

**Weaknesses:**  
- `site.time` forces cache bust every build.  
- Same fallback image for all.  
- Alt text may be too generic.

**Suggestions:**  
- Use per‑file checksum/timestamp for cache busting.  
- Allow per‑project fallback or alt text.

---

### Project Title & Description

```liquid
<div class="project-title">{{ project.title }}</div>
{% if project.description %}
  <div class="muted project-desc">{{ project.description }}</div>
{% endif %}
```

**Strengths:**  
- Conditional avoids empty elements.  
- Clean layout.

**Weaknesses:**  
- Inconsistent card height if description lengths vary.

**Suggestions:**  
- Truncate descriptions.  
- Enforce consistent lengths.

---

### Grid Container

```liquid
<div class="project-grid">
  ... cards ...
</div>
```

**Strengths:**  
- Good use of wrapper for layout.  

**Weaknesses:**  
- Page may get long if many projects.  
- Responsiveness depends on CSS.

**Suggestions:**  
- Ensure responsive design.  
- Consider pagination or “load more.”

---

## General Observations

- No handling if `site.projects` is empty → page may look blank.  
- Thumbnail logic is complex and could confuse new maintainers.  
- Accessibility partially addressed (alt text), but could improve.  
- Performance: scanning `site.static_files` may slow builds.

---

## Suggested Improvements

1. Use `thumbnail:` in project front matter.  
2. Use `slugify` for safer slugs.  
3. Smarter cache busting (per file, not per build).  
4. Handle case of empty project list.  
5. Truncate descriptions for consistency.  
6. Enhance accessibility with custom alt text.  
7. Extract thumbnail logic into include/partial.  
8. Document contributor conventions.  
9. Optimize image sizes and performance.

---
