# `style.scss` Explanation

---

## Front Matter

```scss
---
---
```

- Jekyll front matter (empty) ensures this file is processed by Jekyll before being served as CSS.

---

## Imports

```scss
@import "minima";
```

- Imports styles from the **Minima theme** (the default Jekyll theme).
- All subsequent styles **override or extend** Minima.

---

## Base Tweaks

```scss
body {
  font-family: system-ui, sans-serif;
  line-height: 1.6;
  background: #fff;
  color: #222;
}

h1, h2, h3 {
  margin-top: 1.4em;
  margin-bottom: 0.6em;
  font-weight: 600;
}

p, li {
  margin-bottom: 0.8em;
}
```

- Sets a clean, system font stack with good readability.
- Adjusts heading spacing and font weight.
- Provides consistent bottom margins for text elements.

---

## Header + Footer

```scss
.site-header, .site-footer {
  background: #fafafa;
  border-top: 1px solid #e0e0e0;
  border-bottom: 1px solid #e0e0e0;
  padding: 1em 0;
  text-align: center;
}

.site-footer p {
  font-size: 0.9em;
  color: #666;
}

.wrapper {
  max-width: 960px;
  margin: 0 auto;
  padding: 0 1em;
}

.header-flex {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

- Header/footer have a light gray background and subtle borders.
- Footer text is slightly smaller and lighter in color.
- `.wrapper` centers and constrains content to 960px.
- `.header-flex` uses flexbox to align header elements.

---

## Header Tweaks

```scss
.site-nav a {
  padding: 0.5rem 0.75rem;
  display: inline-block;
}
```

- Navigation links get consistent padding, improving click targets and spacing.

---

## Project Grid + Cards

```scss
.project-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.5rem;
  margin-top: 1.5rem;
}
```

- Defines a **responsive grid** for project cards.

```scss
.project-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  overflow: hidden;
  background: #fff;
  text-align: center;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
  padding: 1rem;
}

.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 16px rgba(0,0,0,0.1);
}
```

- Each card has a white background, rounded corners, and subtle shadow on hover.
- Smooth hover animation provides visual feedback.

```scss
.project-card a {
  text-decoration: none;
  color: inherit;
  display: block;
}

.project-thumb {
  width: 100%;
  height: 160px;
  object-fit: cover;
  background: #f8f8f8;
}

.project-title {
  padding: 0.75rem;
  font-weight: 600;
  font-size: 1rem;
  color: #222;
}

.project-card p {
  margin: 0.5rem 0 1rem;
}
```

- Ensures project links are clickable and styled consistently.
- Thumbnail images are fixed-height with `object-fit: cover`.
- Titles bold and well-spaced; descriptions have tight margins.

---

## Swiper (Gallery) Tweaks

```scss
.swiper {
  width: 100%;
  margin: 1.2rem 0;
}

.swiper .swiper-slide {
  display: flex;
  align-items: center;
  justify-content: center;
}

.swiper .swiper-slide img {
  display: block;
  width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: 6px;
}
```

- Sets gallery width and spacing.
- Centers images inside slides.
- Rounds slide image corners.

---

## Gallery Tweaks

```scss
/* Hide arrows completely */
.swiper-button-prev,
.swiper-button-next {
  display: none !important;
}
```

- Removes navigation arrows (relies on dots and click navigation).

```scss
/* Move dots below slides */
.swiper-pagination {
  position: relative !important;
  margin-top: 12px;
  text-align: center;
}

/* pagination dots */
.gallery .swiper-pagination-bullet {
  background-color: gray;
  opacity: 0.6;
}

/* active dot */
.gallery .swiper-pagination-bullet-active {
  background-color: #555;
  opacity: 1;
}
```

- Positions pagination dots below slides.
- Uses gray inactive dots and darker active dot for clarity.

---

## Critique

✅ **Strengths**:
- Clean, minimal, and consistent styling.
- Responsive project grid adapts to various screen sizes.
- Nice hover animations on cards (subtle and modern).
- Gallery styling integrates smoothly with Swiper.js.

⚠️ **Weaknesses**:
- Arrows disabled → may reduce accessibility for some users.
- Fixed project thumbnail height (160px) could crop images awkwardly.
- Minimal color usage → might feel bland depending on brand identity.

💡 **Suggestions for Improvement**:
1. Allow optional **navigation arrows** for better accessibility.
2. Make project card height **adaptive** or allow aspect-ratio CSS.
3. Introduce **brand accent colors** for links, hover states, and pagination dots.
4. Improve **footer hierarchy** (add nav links, better contrast).
5. Consider **dark mode support**.

---

✅ **Summary**:  
This stylesheet customizes Minima with a project-focused layout and gallery integration. It’s functional and modern but could use more brand identity, accessibility improvements, and visual polish.
