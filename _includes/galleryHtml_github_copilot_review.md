# `gallery.html` Include Explanation

This file defines a reusable Jekyll include that builds an image gallery (with Swiper.js) for a given project.

---

## Liquid (Jekyll) Section

```liquid
{%- comment -%}
Gallery include
----------------------------------
Usage:
  {% include gallery.html slug="project-a" title="Project A" %}
If omitted, it will use page.slug or page.name as a fallback.
{%- endcomment -%}
```

- **Comment block**: documents usage.
- You can call this include with `slug` and `title`.
- If `slug` is not given, it falls back to the page’s `slug` or `name`.

---

```liquid
{%- assign project_slug = include.slug | default: page.slug | default: page.name | split: "." | first -%}
{%- assign project_path = '/assets/projects/' | append: project_slug -%}
```

- `project_slug`: determines which project folder to use, stripping any file extensions.
- `project_path`: builds the asset path, e.g. `/assets/projects/project-a`.

---

```html
<div class="gallery">
  <div class="swiper gallery-swiper">
    <div class="swiper-wrapper">
```
- Outer **`<div class="gallery">`**: wrapper for the gallery.
- Inner **`swiper`** containers are required by Swiper.js.

---

```liquid
{%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
{%- assign screenshots = site.static_files | where_exp: "file", "file.path contains project_path" -%}
```

- `extensions`: allowed image types.
- `screenshots`: filters all static files to only those under the project’s asset path.

---

```liquid
{%- assign numbered_files = "" | split: "" -%}
```
- Initializes an empty array for storing gallery items.

---

```liquid
{%- for file in screenshots -%}
  {%- assign ext = file.extname | remove: "." | downcase -%}
  {%- assign name_no_ext = file.name | remove: file.extname | remove: "." -%}
  {%- assign parts = name_no_ext | split: "-" -%}
  {%- assign last_part = parts | last -%}
  {%- assign number_val = last_part | plus: 0 -%}
```
- Loop through each candidate file.
- Extracts:
  - `ext`: extension (`png`, `jpg`, etc.).
  - `name_no_ext`: filename without extension.
  - `parts`: filename split by `-`.
  - `last_part`: the last segment (expects a number).
  - `number_val`: coerces that to a number (0 if not numeric).

---

```liquid
  {%- if extensions contains ext and number_val > 0 -%}
    {%- assign item = file.path | append: "|" | append: number_val | append: "|" | append: ext -%}
    {%- assign numbered_files = numbered_files | push: item -%}
  {%- endif -%}
{%- endfor -%}
```
- Only include files with:
  - A valid extension.
  - A trailing numeric suffix (`-1.png`, `-2.jpg`, etc.).
- Stores them in `numbered_files` as a pipe-delimited string:  
  `path|number|extension`.

---

```liquid
{%- assign sorted_files = numbered_files | sort_natural -%}
```
- Sorts gallery items in natural order (`1, 2, 3…` instead of `1, 10, 2`).

---

```liquid
{%- for item in sorted_files -%}
  {%- assign parts = item | split: "|" -%}
  <div class="swiper-slide">
    <img src="{{ parts[0] | relative_url }}?v={{ site.time | date: '%s' }}"
         alt="{{ include.title | default: page.title }} screenshot">
  </div>
{%- endfor -%}
```
- For each sorted image:
  - Split into `path`, `number`, and `extension`.
  - Create a Swiper slide with an `<img>`.
  - Cache-bust with a timestamp query (`?v=UNIXTIME`).
  - Adds accessible `alt` text based on the project title.

---

```html
    </div>
    <div class="swiper-pagination"></div>
  </div>
</div>
```
- Closes wrappers.
- Adds pagination dots placeholder.

---

## External Dependencies

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
```
- Loads Swiper CSS + JS from CDN.

---

## JavaScript Section

```js
document.addEventListener("DOMContentLoaded", function () {
  const wrapperSelector = ".gallery-swiper";
  const wrapper = document.querySelector(wrapperSelector);
  if (!wrapper) return;
```
- Waits for DOM ready.
- Selects `.gallery-swiper` container.
- If none, exit.

---

```js
  if (wrapper.querySelectorAll(".swiper-slide").length === 0) {
    const msg = document.createElement("p");
    msg.innerHTML =
      `<em>No gallery images found. Please add files matching <code>-NUMBER.png|.jpg|.jpeg|.svg</code> to <code>{{ project_path }}</code>.</em>`;
    wrapper.parentNode.insertBefore(msg, wrapper);
    wrapper.remove();
    return;
  }
```
- If no slides found:
  - Inserts a helpful `<p>` message.
  - Removes the empty gallery.

---

```js
  const swiper = new Swiper(wrapperSelector, {
    loop: true,
    pagination: { el: wrapperSelector + ' .swiper-pagination', clickable: true },
    slidesPerView: 1,
    spaceBetween: 10,
    keyboard: { enabled: true, onlyInViewport: true } // arrow key navigation
  });
```
- Initializes Swiper:
  - Infinite loop.
  - Pagination dots.
  - One slide visible at a time.
  - Arrow key navigation.

---

```js
  wrapper.addEventListener("click", function (e) {
    if (e.target.tagName.toLowerCase() === "img") {
      const rect = e.target.getBoundingClientRect();
      const clickX = e.clientX - rect.left;
      if (clickX < rect.width / 2) {
        swiper.slidePrev();
      } else {
        swiper.slideNext();
      }
    }
  });
});
```
- Adds click navigation:
  - Clicking **left half** of image → previous slide.
  - Clicking **right half** → next slide.

---

# Summary

- This include dynamically builds a gallery for a project.
- Images must be named with a **numbered suffix**: `screenshot-1.png`, `screenshot-2.jpg`, etc.
- It uses **Swiper.js** for navigation, pagination, and keyboard support.
- Fallback: shows a warning if no valid images exist.
