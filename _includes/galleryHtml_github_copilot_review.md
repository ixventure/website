# Line-by-line explanation of `_includes/gallery.html`

This file is a Jekyll include that builds a project gallery using Swiper.js. Below I show the source and then explain every line in order.

## Source

```liquid
{%- comment -%}
Gallery include
----------------------------------
Usage:
  {% include gallery.html slug="project-a" title="Project A" %}
If omitted, it will use page.slug or page.name as a fallback.
{%- endcomment -%}

{%- assign project_slug = include.slug | default: page.slug | default: page.name | split: "." | first -%}
{%- assign project_path = '/assets/projects/' | append: project_slug -%}

<h2>Gallery</h2>
<div class="gallery">
  <div class="swiper gallery-swiper">
    <div class="swiper-wrapper">
      {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
      {%- assign screenshots = site.static_files | where_exp: "file", "file.path contains project_path" | sort: "path" -%}

      {%- for file in screenshots -%}
        {%- assign ext = file.extname | remove: "." | downcase -%}
        {%- if extensions contains ext and file.name contains "image-" -%}
          <div class="swiper-slide">
            <img src="{{ file.path | relative_url }}?v={{ site.time | date: '%s' }}"
                 alt="{{ include.title | default: page.title }} screenshot">
          </div>
        {%- endif -%}
      {%- endfor -%}
    </div>

    <div class="swiper-pagination"></div>
    <div class="swiper-button-prev" aria-label="Previous slide"></div>
    <div class="swiper-button-next" aria-label="Next slide"></div>
  </div>
</div>

<!-- Swiper resources -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>

<script>
document.addEventListener("DOMContentLoaded", function () {
  const wrapperSelector = ".gallery-swiper";
  const wrapper = document.querySelector(wrapperSelector);
  if (!wrapper) return;

  // If no slides (no images), show a helpful message with exact folder
  if (wrapper.querySelectorAll(".swiper-slide").length === 0) {
    const msg = document.createElement("p");
    msg.innerHTML =
      '<em>No gallery images found. Please add <code>image-*.png|.jpg|.jpeg|.svg</code> to <code>{{ project_path }}</code>.</em>';
    wrapper.parentNode.insertBefore(msg, wrapper);
    wrapper.remove();
    return;
  }

  new Swiper(wrapperSelector, {
    loop: true,
    pagination: { el: wrapperSelector + ' .swiper-pagination', clickable: true },
    navigation: { nextEl: wrapperSelector + ' .swiper-button-next', prevEl: wrapperSelector + ' .swiper-button-prev' },
    slidesPerView: 1,
    spaceBetween: 10
  });
});
</script>

```

## Line-by-line explanation

### 1

```
{%- comment -%}
```
Start of a Liquid comment block. Everything until `{%- endcomment -%}` is ignored by Jekyll at build time. Used here to document how to use the include.

### 2

```
Gallery include
```
Commented documentation header inside the Liquid comment.

### 3

```
----------------------------------
```
Commented documentation header inside the Liquid comment.

### 4

```
Usage:
```
Part of the comment: shows how to call this include from a Jekyll page.

### 5

```
  {% include gallery.html slug="project-a" title="Project A" %}
```
Utility or closing line: ties up the previous block.

### 6

```
If omitted, it will use page.slug or page.name as a fallback.
```
Utility or closing line: ties up the previous block.

### 7

```
{%- endcomment -%}
```
End of the Liquid comment block.

### 8

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 9

```
{%- assign project_slug = include.slug | default: page.slug | default: page.name | split: "." | first -%}
```
Define `project_slug` for this gallery. It uses the value passed to the include (`include.slug`) if present, otherwise falls back to `page.slug` or `page.name`. Finally it splits on `.` and takes the first part to strip file extensions.

### 10

```
{%- assign project_path = '/assets/projects/' | append: project_slug -%}
```
Builds `project_path` by appending the `project_slug` to the base folder `/assets/projects/`. This is the folder the gallery will search for images in.

### 11

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 12

```
<h2>Gallery</h2>
```
HTML: top-level heading for the gallery section.

### 13

```
<div class="gallery">
```
HTML: wrapper element with class `gallery` for styling and scoping.

### 14

```
  <div class="swiper gallery-swiper">
```
HTML: the Swiper container. `swiper` is Swiper's root class and `gallery-swiper` provides a local selector used later in JavaScript to initialize the slider.

### 15

```
    <div class="swiper-wrapper">
```
HTML: Swiper's wrapper for slides. Child `.swiper-slide` elements go inside this container.

### 16

```
      {%- assign extensions = "png,jpg,jpeg,svg" | split: "," -%}
```
Creates a Liquid array named `extensions` by splitting the string `png,jpg,jpeg,svg`. Used to whitelist which file extensions to include as slides.

### 17

```
      {%- assign screenshots = site.static_files | where_exp: "file", "file.path contains project_path" | sort: "path" -%}
```
Collects site static files whose `file.path` contains `project_path`. `site.static_files` returns all files in the `assets/` (and other static) folders. `where_exp` filters this list and `sort: "path"` orders them.

### 18

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 19

```
      {%- for file in screenshots -%}
```
Starts a Liquid `for` loop iterating over each `file` object found in the `screenshots` list.

### 20

```
        {%- assign ext = file.extname | remove: "." | downcase -%}
```
Gets the file's extension from `file.extname`, removes the leading dot (`.`), and converts it to lowercase. Result stored in `ext` for extension checks.

### 21

```
        {%- if extensions contains ext and file.name contains "image-" -%}
```
Conditional: only proceed if `ext` is in the `extensions` whitelist AND the file's `name` contains `image-`. This enforces both extension and filename pattern requirements (e.g., `image-1.png`).

### 22

```
          <div class="swiper-slide">
```
HTML: start of a single Swiper slide. Each matched image gets wrapped in this container.

### 23

```
            <img src="{{ file.path | relative_url }}?v={{ site.time | date: '%s' }}"
```
Image tag for the slide. `file.path | relative_url` produces the correct URL respecting `baseurl`. Appends `?v={{ site.time | date: '%s' }}` to the URL to force cache-busting on each build (site.time is replaced at build time).

### 24

```
                 alt="{{ include.title | default: page.title }} screenshot">
```
`alt` attribute for accessibility. Uses the `include.title` if provided, otherwise falls back to `page.title`, then adds the word 'screenshot'. Good for screen readers and SEO.

### 25

```
          </div>
```
Closing a previously opened HTML container.

### 26

```
        {%- endif -%}
```
End of the conditional that checks filename and file extension.

### 27

```
      {%- endfor -%}
```
End of the `for` loop that generated slides.

### 28

```
    </div>
```
Closing a previously opened HTML container.

### 29

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 30

```
    <div class="swiper-pagination"></div>
```
Element where Swiper will render pagination indicators (dots) if pagination is enabled.

### 31

```
    <div class="swiper-button-prev" aria-label="Previous slide"></div>
```
Navigation buttons for previous/next. They include `aria-label` attributes (where present) for accessibility.

### 32

```
    <div class="swiper-button-next" aria-label="Next slide"></div>
```
Navigation buttons for previous/next. They include `aria-label` attributes (where present) for accessibility.

### 33

```
  </div>
```
Closing a previously opened HTML container.

### 34

```
</div>
```
Closing a previously opened HTML container.

### 35

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 36

```
<!-- Swiper resources -->
```
Comment marking the inclusion of external Swiper CSS/JS resources.

### 37

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.css" />
```
Loads Swiper's stylesheet from jsDelivr CDN (version 11 as pinned). Required for Swiper's default styles.

### 38

```
<script src="https://cdn.jsdelivr.net/npm/swiper@11/swiper-bundle.min.js"></script>
```
Loads Swiper's JavaScript from jsDelivr CDN. Required to initialize and run the slider.

### 39

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 40

```
<script>
```
Starts an inline script block executed in the browser.

### 41

```
document.addEventListener("DOMContentLoaded", function () {
```
Waits for DOMContentLoaded before running the initialization code, ensuring elements are present in the DOM.

### 42

```
  const wrapperSelector = ".gallery-swiper";
```
Defines a CSS selector string to target the Swiper container (`.gallery-swiper`).

### 43

```
  const wrapper = document.querySelector(wrapperSelector);
```
Selects the Swiper container element from the DOM. If not found, the script will return early.

### 44

```
  if (!wrapper) return;
```
Guard clause: if the `.gallery-swiper` element doesn't exist on the page, stop executing the script.

### 45

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 46

```
  // If no slides (no images), show a helpful message with exact folder
```
Utility or closing line: ties up the previous block.

### 47

```
  if (wrapper.querySelectorAll(".swiper-slide").length === 0) {
```
Checks how many `.swiper-slide` elements exist inside the wrapper. If zero, it will show a helpful message for the developer/site author.

### 48

```
    const msg = document.createElement("p");
```
Creates a new `<p>` element to hold the 'no images found' message.

### 49

```
    msg.innerHTML =
```
Sets the inner HTML of the message paragraph. The string includes a Liquid variable `{{ project_path }}`, which Jekyll will substitute at build time so the message shows the correct folder path. The message instructs where to add files.

### 50

```
      '<em>No gallery images found. Please add <code>image-*.png|.jpg|.jpeg|.svg</code> to <code>{{ project_path }}</code>.</em>';
```
Utility or closing line: ties up the previous block.

### 51

```
    wrapper.parentNode.insertBefore(msg, wrapper);
```
Inserts the message `<p>` before the wrapper element so it is visible in the page flow.

### 52

```
    wrapper.remove();
```
Removes the empty gallery wrapper from the DOM (since there are no slides to show).

### 53

```
    return;
```
Stops further execution of the script after showing the message.

### 54

```
  }
```
Utility or closing line: ties up the previous block.

### 55

```
(blank line)
```
Blank line to improve readability and separate logical blocks.

### 56

```
  new Swiper(wrapperSelector, {
```
Initializes a new Swiper instance targeting the `wrapperSelector`.

### 57

```
    loop: true,
```
Enables continuous looping of slides so navigation cycles infinitely.

### 58

```
    pagination: { el: wrapperSelector + ' .swiper-pagination', clickable: true },
```
Element where Swiper will render pagination indicators (dots) if pagination is enabled.

### 59

```
    navigation: { nextEl: wrapperSelector + ' .swiper-button-next', prevEl: wrapperSelector + ' .swiper-button-prev' },
```
Navigation buttons for previous/next. They include `aria-label` attributes (where present) for accessibility.

### 60

```
    slidesPerView: 1,
```
Sets how many slides are visible at once. `1` means one slide per view (typical for a simple gallery).

### 61

```
    spaceBetween: 10
```
Pixel spacing between slides; `10` adds a small gap.

### 62

```
  });
```
Utility or closing line: ties up the previous block.

### 63

```
});
```
Utility or closing line: ties up the previous block.

### 64

```
</script>
```
End of the inline script block.
