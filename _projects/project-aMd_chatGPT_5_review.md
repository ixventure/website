# Line-by-Line Review of `_projects/project-a.md`

**Commit reviewed:** `3f6199c2ea7fd3e717c629caad40c7d66f3dbcba`

---

## 1. Front Matter

```markdown
---
title: Project A
slug: project-a
layout: project
---
```

- YAML front matter for Jekyll; controls the page title, URL (via `slug`), and layout.  
- **title**: `Project A` — clean and consistent with the filename.  
- **slug**: `project-a` — matches the folder / permalink convention used by the site.  
- **layout**: `project` — this expects `_layouts/project.html` to provide the per-project wrapper (title render, gallery include, etc.).

---

## 2. Content (body)

```markdown
This is **Project A**, an example project.

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vivamus lacinia odio vitae vestibulum vestibulum.

- Feature 1
- Feature 2
- Feature 3
```

Line-by-line notes:
- `This is **Project A**, an example project.` — Good short intro. Consider replacing with a one- or two-sentence summary of what the project does (audience, problem solved, tech used).
- The following paragraph is placeholder ("Lorem ipsum..."). Replace with real descriptive content that explains the project's context and notable outcomes or links to a demo/repo as appropriate.
- The feature list is valid Markdown and will render as a simple unordered list. If you want them styled or displayed in columns, handle that in `_layouts/project.html` or provide CSS classes via an HTML list.

---

## 3. Rendering / Integration

- This file will be parsed by Jekyll and rendered with `_layouts/project.html`. Ensure that the layout includes the gallery include (if you want images shown), or add an `{% include gallery.html slug="project-a" title="Project A" %}` call here or in the layout if you prefer.
- If you rely on `site.projects` or other collections, confirm that `_config.yml` defines the `projects` collection and that permalinks/collections are configured consistently.

---

## Summary

This file is syntactically correct and ready to be turned into real content. Suggested next steps:
- Replace the placeholder paragraph with a short project description (2–4 sentences).
- Optionally add links (repo/demo) and enrich the features list with brief explanations.
- If you want the gallery to auto-populate, ensure image assets exist under `assets/projects/project-a/` (they do), and that `_includes/gallery.html` picks them up.


**Ready for review and teaching purposes!**
