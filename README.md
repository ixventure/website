# IxVenture Studio — Jekyll template

This repository contains a small Jekyll template used by IxVenture Studio.
It provides a projects collection and a lightweight gallery include that
auto-discovers images inside `assets/projects/<slug>/`.

## Quick notes

- Projects live in `_projects/` and must include front matter:
  - `title` (string)
  - `description` (string)
  - `slug` (string, matching directory under `assets/projects/`)
  - `thumbnail` (optional path to a thumbnail image)
  - `layout: project`

- Project images should be put in `assets/projects/<slug>/` and named
  consistently (e.g. `screenshot-1.png`, `screenshot-2.png`, etc.) to make
  re-use and searching predictable.

- The gallery include (`_includes/gallery.html`) will loop over
  `site.static_files` and include any file found under `assets/projects/<slug>/`.
  It adds a cache-busting query string using `site.time`.

## Local development

```bash
# Install (if using bundler)
bundle install

# Serve locally (restart if you add new static files that Jekyll doesn't pick up)
bundle exec jekyll serve --livereload
```

If you find that a newly added static image doesn't appear during `jekyll serve`,
restart the server. Cache-busting query strings are included so browsers will
fetch new images after site rebuilds.

## Deploy

This template is ready for GitHub Pages or other static hosts (Cloudflare in front is okay).
If Cloudflare is used, consider setting `Cache-Control: no-cache` for HTML and using
aggressive caching only for known fixed asset names, or rely on the cache-busting query strings.
