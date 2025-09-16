# Line-by-Line Review of `_layouts/project.html`

**Commit reviewed:** `feed96c10b049cb4085d35aab23c5a15044d7bc2`

---

## 1. Front Matter

```html
---
layout: default
---
```
- YAML front matter for Jekyll.
- Sets the base layout to `default.html`, so this template inherits from it.

---

## 2. Article Container

```html
<article class="project">
```
- Starts an HTML `<article>` with class "project" for semantic grouping and styling.

---

## 3. Project Title

```html
  <header>
    <h1>{{ page.title }}</h1>
  </header>
```
- Header section with the project’s title, pulled from page metadata.

---

## 4. Main Project Content

```html
  <section class="project-content">
    {{ content }}
  </section>
```
- Section for the main body/text of the project.
- Displays the page’s Markdown or HTML content.

---

## 5. Project Gallery

```html
  <section class="project-gallery">
    {% include gallery.html slug=page.slug title=page.title %}
  </section>
```
- Section for a gallery of images.
- Uses the reusable `gallery.html` include, passing the page’s slug and title.

---

## 6. Benefits Section (Conditional)

```html
  {% if page.benefits %}
  <section class="project-benefits">
    <h2>Benefits</h2>
    <ul>
      {% for benefit in page.benefits %}
        <li>{{ benefit }}</li>
      {% endfor %}
    </ul>
  </section>
  {% endif %}
```
- If `benefits` are defined on the page, renders a section titled "Benefits".
- Loops through each benefit and displays as a list item.

---

## 7. End of Article

```html
</article>
```
- Closes the main article element.

---

## Summary

This layout:
- Inherits navigation, header, footer, and other global elements from `default.html`.
- Displays the project title and main content.
- Shows a gallery of project images using the gallery include.
- Optionally lists benefits provided in the page’s front matter.
- Uses clean semantic HTML for accessibility and styling.

**Ready for student review and documentation!**
