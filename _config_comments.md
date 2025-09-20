# `_config.yml` Explanation

---

## Site Identity

```yaml
title: IxVenture
description: Building something amazing with AI
```
- **`title`** → Main site title (used in layouts, `<title>` tag, etc.).  
- **`description`** → Subtitle/summary shown in metadata and templates.

---

## Repo-mode Settings

```yaml
url: "https://bestape.github.io"
baseurl: "/ixv-jekyll-minima-template"
```
- **`url`** → Canonical site root (needed for absolute links, RSS, SEO).  
- **`baseurl`** → Subpath for project sites on GitHub Pages (here: `/ixv-jekyll-minima-template`).  
- Used together, full URLs resolve to:  
  `https://bestape.github.io/ixv-jekyll-minima-template/...`

```yaml
# Use empty baseurl by default, but allow GitHub Pages to override
# baseurl: "" 
# url: "" 
```
- Comments explain alternate config for local or production use.

---

## Theme

```yaml
theme: minima
```
- Uses Jekyll’s **Minima theme** as the base.

---

## Versioning

```yaml
version: 0.1.14
```
- Explicit **site version number**, helpful for documentation, cache-busting, or CI/CD references.

---

## Collections

```yaml
collections:
  projects:
    output: true
    permalink: /projects/:path/
```
- Defines a **custom collection** named `projects`.  
- `output: true` → generates pages for items in `_projects/`.  
- `permalink` pattern → `/projects/<filename>/`.

---

## Includes

```yaml
include:
  - assets
  - version.json
```
- Ensures Jekyll processes and copies `assets/` and `version.json` into the output `_site/` folder.  
- Normally, Jekyll ignores non-page/non-post files unless explicitly included.

---

## Critique

✅ **Strengths**:
- Clear and minimal configuration.  
- Proper GitHub Pages setup (`url` + `baseurl`).  
- Version tracking adds professionalism.  
- Projects collection is well-structured with clean permalinks.

⚠️ **Weaknesses**:
- No plugins enabled (could limit functionality).  
- Hardcoded `url` may cause confusion when testing locally.  
- Version number maintained manually (can drift from Git history).  
- Metadata (title/description) is very generic.

💡 **Suggestions for Improvement**:
1. Add `plugins:` for SEO (`jekyll-seo-tag`), sitemap (`jekyll-sitemap`), or feeds (`jekyll-feed`).  
2. Use environment variables or separate `_config_dev.yml` for local vs production.  
3. Automate version number injection from Git tags or commits.  
4. Expand metadata (author, social links, language, etc.).  
5. Consider `defaults:` for setting layout/metadata across collections.

---

✅ **Summary**:  
`_config.yml` sets up a lean, GitHub Pages–ready Jekyll site with a projects collection. It’s functional and minimal but could benefit from richer metadata, plugin support, and automated versioning.
