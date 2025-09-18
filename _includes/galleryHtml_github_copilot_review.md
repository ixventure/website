# Line-by-Line Review of `_includes/gallery.html`

**Commit reviewed:** `0a65da925df6a2b42498c848295aac9c11db6bc3`  

---

## 1. Include Tag

```liquid
{% include gallery.html slug="project-b" title="Project B" %}
```

- This is a **Jekyll include statement**.  
- It pulls in the file `_includes/gallery.html`.  
- The `slug="project-b"` argument tells the gallery which project’s images/content to load.  
- The `title="Project B"` argument provides a human-readable title for the gallery section.

---

## 2. Purpose

- Lets you reuse a single gallery template for multiple projects.  
- Avoids duplication: instead of hardcoding HTML in each project page, the gallery logic lives in `_includes/gallery.html`.  
- Easier to maintain and update.

---

## 3. Key Takeaways

- **Separation of concerns:** content (Markdown files) stays separate from display logic (HTML include).  
- **Scalability:** adding a new project gallery is as simple as calling the include with a new slug/title.  
