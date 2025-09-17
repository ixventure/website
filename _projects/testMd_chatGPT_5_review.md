# Line-by-Line Review of `_projects/test.md`

**Commit reviewed:** `e86f009e403cc2a4466c2f9a0548902e47511c96`

---

## 1. Front Matter

```markdown
---
title: Project B
slug: test
layout: project
---
```
- YAML front matter declaring metadata.
- **title**: `Project B` (note: mismatch with filename "test.md"; may be intentional placeholder).
- **slug**: `test` — this sets the URL/permalink segment for this project.
- **layout**: `project` — uses `_layouts/project.html` for rendering.

---

## 2. Content (body)

```markdown
# Test

This is **Test**, another example project.

Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin.

- Benefit 1
- Benefit 2
- Benefit 3
```

Line-by-line notes:
- `# Test` — Top-level heading. Redundant with `title: Project B`; clarify naming consistency (Project B vs Test).
- `This is **Test**, another example project.` — Short introduction with bold formatting.
- Placeholder Latin content (“Cras sit amet…”). Replace with actual descriptive text for production.
- Unordered list of benefits is valid Markdown; will render as a bullet list.

---

## 3. Rendering / Integration

- Layout will be provided by `_layouts/project.html`, which is consistent with the other projects.
- The slug is `test`; unless you want a permanent `/test/` URL, consider aligning slug and filename with the actual project name for consistency.

---

## Summary

This file builds correctly but has some inconsistencies:
- **Title vs. filename vs. heading mismatch**: Title is "Project B", filename is `test.md`, heading is `# Test`. Standardize one naming convention.
- Replace placeholder content with a real description and benefits.
- Metadata is structurally correct, but should be cleaned up for clarity.

**Ready for review and teaching purposes!**
