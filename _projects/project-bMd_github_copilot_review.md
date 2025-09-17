# Line-by-Line Review of `_projects/project-b.md`

**Commit reviewed:** `b619aea0d111db045cc010d50809f41c267a260c`

---

## 1. Front Matter

```markdown
---
title: Project B
slug: project-b
layout: project
---
```
- YAML front matter for Jekyll.
- Sets the title to "Project B".
- Sets the slug to "project-b" (used for URLs and gallery includes).
- Sets the layout to `project`, which uses `_layouts/project.html`.

---

## 2. Project Description

```markdown
This is **Project B**, another example project.
```
- Project summary/introduction.
- Uses Markdown bold for emphasis.

---

## 3. Main Content

```markdown
Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin.
```
- Placeholder descriptive text (Latin), commonly used for layout demonstration.

---

## 4. Benefits List

```markdown
- Benefit 1
- Benefit 2
- Benefit 3
```
- Markdown unordered list of project benefits.

---

## Summary

This file:
- Declares metadata so Jekyll builds the page with the correct title, URL, and layout.
- Presents a short description and Markdown-formatted benefit list.
- Will be rendered by `_layouts/project.html` which adds title, gallery, and (optionally) benefits.

**Ready for review and teaching purposes!**
