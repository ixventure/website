# Line-by-Line Review of `_layouts/default.html`

**Commit reviewed:** `7c17cf419e74cf2cf27c71bd41ee6832edbe99ad`

---

## 1. Document and HTML Setup

```html
<!DOCTYPE html>
<html lang="{{ page.lang | default: site.lang | default: 'en' }}">
```
- Declares the document type and sets the HTML language using page or site variable, defaulting to English.

---

## 2. Head Section

```html
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
```
- Sets metadata for character encoding, compatibility, and responsive design.

```html
    <title>{{ page.title | escape }} - {{ site.title | escape }}</title>
    <meta name="description" content="{{ page.excerpt | default: site.description | strip_html | normalize_whitespace | truncate: 160 | escape }}">
```
- Title uses page and site titles.
- Description uses page excerpt, falls back to site description, strips HTML, normalizes whitespace, and truncates to 160 characters for SEO.

```html
    <link rel="stylesheet" href="{{ '/assets/css/style.css' | relative_url }}">
```
- Loads the main CSS stylesheet, using Jekyll’s `relative_url` filter.

---

## 3. Toast Notification Styles

```html
    <style>
      /* small toast styles */
      #update-toast {
        display: none;
        position: fixed;
        top: 1rem;
        right: 1rem;
        background: #222;
        color: #fff;
        padding: 0.75rem 1rem;
        border-radius: 0.5rem;
        box-shadow: 0 4px 12px rgba(0,0,0,0.3);
        z-index: 9999;
        animation: slideDown 0.3s ease-out;
      }
      #update-toast button { margin-left: 1rem; background: #4CAF50; border: none; padding: 0.4rem 0.75rem; border-radius: 0.25rem; color: white; cursor: pointer; }
      #update-toast button:hover { background: #45a049; }
      @keyframes slideDown { from { transform: translateY(-20px); opacity: 0; } to { transform: translateY(0); opacity: 1; } }
    </style>
```
- Inline CSS for the update toast notification (a popup for new version alerts).
- Styles position, color, shadow, button, and animation.

---

## 4. Body and Header

```html
  </head>
  <body>
    <header class="site-header" role="banner">
      <div class="wrapper header-flex">
        <a class="site-title" rel="author" href="{{ '/' | relative_url }}">{{ site.title | escape }}</a>
        <nav class="site-nav">
          <a href="{{ '/projects/' | relative_url }}">Projects</a>
        </nav>
      </div>
    </header>
```
- The header contains the site title (link to home) and a navigation bar with a link to "Projects".

---

## 5. Main Content Area

```html
    <main class="page-content" aria-label="Content">
      <div class="wrapper">
        {{ content }}
      </div>
    </main>
```
- Main content area for page content, wrapped for consistent styling.

---

## 6. Footer

```html
    <footer class="site-footer">
      <div class="wrapper">
        <p>
          IxVenture site — powered by Jekyll.<br>
          Theme is a FLOSS fork of Minima — contributions welcome!<br>
          Version: {{ site.version }}
        </p>
      </div>
    </footer>
```
- Footer credits Jekyll, notes open-source theme, and displays site version.

---

## 7. Update Toast Element

```html
    <!-- Update toast -->
    <div id="update-toast">
      🔄 New version available.
      <button id="reload-btn">Reload</button>
    </div>
```
- Hidden toast notification shown when a new version is available.

---

## 8. JavaScript: Update Notification Logic

```html
    <script>
      document.addEventListener('DOMContentLoaded', function () {
        const currentBuild = "{{ site.time | date_to_xmlschema }}";
        const toast = document.getElementById('update-toast');
        const reloadBtn = document.getElementById('reload-btn');

        async function checkForUpdateOnce() {
          try {
            const res = await fetch('/version.json', { cache: 'no-store' });
            if (!res.ok) return;
            const data = await res.json();
            if (data.build && data.build !== localStorage.getItem('lastBuild')) {
              toast.style.display = 'block';
              localStorage.setItem('newBuild', data.build);
            }
          } catch (e) {
            console.debug('Version check failed', e);
          }
        }

        if (reloadBtn) {
          reloadBtn.addEventListener('click', function () {
            localStorage.setItem('lastBuild', localStorage.getItem('newBuild'));
            location.reload(true);
          });
        }

        // initial check + periodic
        checkForUpdateOnce();
        setInterval(checkForUpdateOnce, 60 * 1000);
      });
    </script>
```
- On page load, defines `currentBuild` using the site's build time.
- Gets references to toast and reload button.
- `checkForUpdateOnce()` fetches `/version.json` (no cache) to check if a newer build is available.
  - If so, shows the toast and saves the new build info.
  - If reload is clicked, updates `lastBuild` and reloads the page.
- Checks for updates once on load, then every minute.

---

## 9. End of Document

```html
  </body>
</html>
```
- Closes body and html tags.

---

## Summary

This layout:
- Sets up the document structure, SEO, and responsive design.
- Displays site navigation and content.
- Credits open-source technologies and shows version info.
- Provides a system for notifying users when a new version is available, prompting them to reload for updates.
- Uses Jekyll/Liquid to populate content and metadata.

**Ready for use in your teaching materials!**