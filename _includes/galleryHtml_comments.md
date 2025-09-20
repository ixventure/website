# `gallery_v0.3.html` Explanation

---

## Header Comment

```liquid
{%- comment -%}
Gallery include (v0.3)
----------------------------------
Usage:
  {% include gallery.html slug="project-a" title="Project A" %}
If omitted, it will use page.slug or page.name as a fallback.

Changelog v0.3:
- Added support for fallback filenames without numbers.
- Cache-busting now uses file modification time (if available).
- Alt text can use filename as a fallback if no title provided.
- Added graceful <noscript> fallback.
- Added "next steps" section in comments for future improvements.
{%- endcomment -%}
```

- Documents usage.
- Lists changes since earlier versions (v0.3 notes).

---

## Liquid Variables

```liquid
{%- assign project_slug = include.slug | default: page.slug | default: page.name | split: "." | first -%}
{%- assign project_path = '/assets/projects/' | append: project_slug -%}
```

- Chooses the project slug from:
  1. `include.slug`
  2. `page.slug`
  3. `page.name`
- Removes extensions.
- Builds path `/assets/projects/<slug>`.

---

## HTML Structure

```html
<div class="gallery">
  <div class="swiper gallery-swiper">
    <div class="swiper-wrapper">
```

- Outer wrapper.
- Swiper container and wrapper for slides.

---

## Allowed Extensions & File Filtering

```liquid
{%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
{%- assign screenshots = site.static_files | where_exp: "file", "file.path contains project_path" -%}
{%- assign numbered_files = "" | split: "" -%}
{%- assign fallback_files = "" | split: "" -%}
```

- Valid extensions = PNG/JPG/JPEG/SVG.
- Filters `site.static_files` to project path.
- Creates two arrays:  
  - `numbered_files` (like `-1.png` etc.)  
  - `fallback_files` (non-numbered).

---

## Loop Over Files

```liquid
{%- for file in screenshots -%}
  {%- assign ext = file.extname | remove: "." | downcase -%}
  {%- assign name_no_ext = file.name | remove: file.extname | remove: "." -%}
  {%- assign parts = name_no_ext | split: "-" -%}
  {%- assign last_part = parts | last -%}
  {%- assign number_val = last_part | plus: 0 -%}
```

- Extracts extension, filename, and checks if filename ends with a number.

---

## Categorize Files

```liquid
  {%- if extensions contains ext and number_val > 0 -%}
    {%- assign item = file.path | append: "|" | append: number_val | append: "|" | append: ext -%}
    {%- assign numbered_files = numbered_files | push: item -%}
  {%- elsif extensions contains ext -%}
    {%- assign item = file.path | append: "|9999|" | append: ext -%}
    {%- assign fallback_files = fallback_files | push: item -%}
  {%- endif -%}
{%- endfor -%}
```

- If file has extension + numeric suffix → goes into `numbered_files`.
- If only extension (no number) → goes into `fallback_files` with artificial index `9999` (so numbered ones sort first).

---

## Sort & Merge

```liquid
{%- assign all_files = numbered_files | concat: fallback_files -%}
{%- assign sorted_files = all_files | sort_natural -%}
```

- Merge numbered and fallback files.
- Sort in natural order.

---

## Build Slides

```liquid
{%- for item in sorted_files -%}
  {%- assign parts = item | split: "|" -%}
  {%- assign file_path = parts[0] -%}
  {%- assign file_ext = parts[2] -%}
  {%- assign file_name = file_path | split: "/" | last -%}
  <div class="swiper-slide">
    <img src="{{ file_path | relative_url }}?v={{ site.time | date: '%s' }}"
         alt="{{ include.title | default: page.title | default: file_name }} screenshot">
  </div>
{%- endfor -%}
```

- Iterates over sorted items.
- Gets path, extension, and filename.
- Creates `<img>` tag:
  - URL with cache-busting timestamp.
  - Alt text = `title` → `page.title` → fallback to filename.

---

## Pagination + Close Wrappers

```html
    </div>
    <div class="swiper-pagination"></div>
  </div>
```

- Adds Swiper pagination dots.

---

## Noscript Fallback

```html
  <noscript>
    <p><em>Gallery requires JavaScript to view. Below are static images:</em></p>
    <ul>
      {%- for item in sorted_files -%}
        {%- assign parts = item | split: "|" -%}
        {%- assign file_path = parts[0] -%}
        {%- assign file_name = file_path | split: "/" | last -%}
        <li><img src="{{ file_path | relative_url }}" alt="{{ include.title | default: page.title | default: file_name }}"></li>
      {%- endfor -%}
    </ul>
  </noscript>
</div>
```

- Provides `<noscript>` fallback:
  - If JS disabled, still shows a static list of `<img>`.

---

## External Dependencies

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
```

- Loads Swiper CSS/JS from CDN.

---

## JavaScript Logic

```js
document.addEventListener("DOMContentLoaded", function () {
  const wrapperSelector = ".gallery-swiper";
  const wrapper = document.querySelector(wrapperSelector);
  if (!wrapper) return;
```

- Wait for DOM.
- Select `.gallery-swiper`.

---

### Handle Empty Galleries

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

- If no slides → injects message → removes empty wrapper.

---

### Initialize Swiper

```js
  const swiper = new Swiper(wrapperSelector, {
    loop: true,
    pagination: { el: wrapperSelector + ' .swiper-pagination', clickable: true },
    slidesPerView: 1,
    spaceBetween: 10,
    keyboard: { enabled: true, onlyInViewport: true }
  });
```

- Initializes Swiper with looping, pagination, spacing, and keyboard support.

---

### Click Navigation

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

- Clicking **left half** of image → previous slide.
- Clicking **right half** → next slide.

---

## Suggested Next Steps (v0.3+)

```liquid
{%- comment -%}
Suggested Next Steps for v0.3+:
----------------------------------
1. Performance: Avoid scanning all static files — use YAML front matter or a _data file instead.
2. Accessibility: Allow per-image alt text via metadata (e.g., alt captions in YAML).
3. Caching: Use file hashes or last-modified times for cache busting, instead of site build time.
4. Resilience: Consider bundling Swiper locally instead of relying on CDN.
5. Graceful degradation: Enhance <noscript> block with better styling.
6. Security: Avoid leaking project_path in error messages for production builds.
{%- endcomment -%}
```

- Lists improvement opportunities for future versions.

---

✅ **Summary**:  
v0.3 improves robustness (fallback files, better alt text, `<noscript>` fallback) while leaving room for optimization (performance, caching, accessibility).
