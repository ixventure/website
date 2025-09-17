# Line-by-Line Review of `_config.yml`

**File Purpose:**  
This file configures how Jekyll builds and serves the site. It controls metadata, theming, collections, and includes.

---

## File Content

```yaml
title: IxVenture
description: Building something amazing with AI

# Use empty baseurl by default, but allow GitHub Pages to override
baseurl: "" 
url: "" 

theme: minima

# Site version
version: 0.1.11

collections:
  projects:
    output: true
    permalink: /projects/:path/

# Ensure static images are included
include:
  - assets

```

---

## Breakdown

### Metadata
```yaml
title: IxVenture
description: Building something amazing with AI
```
- Sets the site’s title and description, used in layouts and SEO tags.

### Base URLs
```yaml
baseurl: "" 
url: "" 
```
- `baseurl`: Empty means site runs at the root (`/`). GitHub Pages can override this if needed.  
- `url`: Empty here but should be set to your production domain (`https://ixventure.studio`) for SEO and absolute links.

### Theme
```yaml
theme: minima
```
- Uses Jekyll’s default **minima** theme as a foundation.  

### Version
```yaml
version: 0.1.11
```
- Custom version marker for the site. Helpful for tracking deployments.

### Collections
```yaml
collections:
  projects:
    output: true
    permalink: /projects/:path/
```
- Defines a custom collection called `projects`.  
- `output: true` ensures each project is built into HTML.  
- `permalink` sets clean URLs like `/projects/project-a/`.

### Includes
```yaml
include:
  - assets
```
- Ensures the `assets/` folder (CSS, images) is processed and deployed with the site.

---

## Suggestions
- Set `url: "https://ixventure.studio"` for production to improve SEO and canonical URLs.  
- Consider adding `plugins:` section if using SEO or sitemap generators.  
- Use `_config.dev.yml` vs `_config.prod.yml` split if you want different configs for local vs production.

---

**Reviewed for educational literacy by ChatGPT‑5.**
