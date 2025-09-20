# default.html Line-by-Line Explanation

> Detailed breakdown of the template structure and behavior.

```html
<!DOCTYPE html>
```
Defines the document type and version of HTML.

```html
<html lang="{{ page.lang | default: site.lang | default: 'en' }}">
```
Opens the HTML document, sets the language dynamically based on page or site config, defaults to English.

```html
<head>
```
Head section begins: metadata, title, styles, etc.

```html
<meta charset="utf-8">
```
Specifies UTF-8 character encoding.

```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```
Ensures compatibility mode is Edge in IE browsers.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```
Makes layout responsive by controlling viewport scaling.

```html
<title>{{ page.title | escape }} - {{ site.title | escape }}</title>
```
Page title combines the page title with the site title.

```html
<meta name="description" content="{{ page.excerpt | default: site.description | strip_html | normalize_whitespace | truncate: 160 | escape }}">
```
Sets the meta description dynamically with safe formatting and length limits.

```html
<link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
```
Links to the main stylesheet for styling.

```html
<style> ... </style>
```
Inline CSS defining styles for the update toast notification UI.

```html
</head>
```
Head section ends.

```html
<body>
```
Body begins: visible content goes here.

```html
<header class="site-header" role="banner">
```
Header section with banner role for accessibility.

```html
<div class="wrapper header-flex">
```
Wrapper container for header layout.

```html
<a class="site-title" rel="author" href="{{ '/' | relative_url }}">{{ site.title | escape }}</a>
```
Site title link points to home page, displays site title.

```html
<nav class="site-nav">
```
Navigation bar section.

```html
<a href="{{ '/projects/' | relative_url }}">Projects</a>
```
Navigation link to the Projects page.

```html
</nav></div></header>
```
Closes navigation, wrapper, and header.

```html
<main class="page-content" aria-label="Content">
```
Main content area with ARIA label for accessibility.

```html
<div class="wrapper">
```
Wrapper for main content.

```html
{{ content }}
```
Dynamic content injected by Jekyll for this page.

```html
</div></main>
```
Closes main content wrapper and section.

```html
<footer class="site-footer">
```
Footer begins.

```html
<div class="wrapper">
```
Wrapper for footer content.

```html
<p> IxVenture site — powered by Jekyll.<br> Theme is a FLOSS fork of Minima — contributions welcome!<br> Version: {{ site.version }} </p>
```
Footer text with project credits and version number.

```html
</div></footer>
```
Closes footer wrapper and footer section.

```html
<div id="update-toast"> 🔄 New version available. <button id="reload-btn">Reload</button> </div>
```
Hidden toast notification shown when a new version of the site is available.

```html
<script> ... </script>
```
JavaScript for checking updates via version.json, showing toast, and handling reload.

```html
</body>
```
Closes body.

```html
</html>
```
Closes HTML document.

## Next Steps Critique

- Accessibility: Consider adding `aria-live` to the update toast so screen readers announce it.
- Progressive Enhancement: Provide a fallback if JavaScript fails or version.json cannot be fetched.
- Performance: Move inline CSS for the toast into the external stylesheet to keep styles centralized.
- Version Handling: Consider expiring old cache aggressively or adding a timestamp query to version.json fetches.
- UI: Add a close button to dismiss the toast without reloading.
- Security: Ensure version.json is served with proper CORS and caching headers.
