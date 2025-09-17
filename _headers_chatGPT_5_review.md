# Line-by-Line Review of `_headers`

**File Purpose:**  
Controls HTTP response headers for files deployed on the site (commonly used in Netlify).  
These headers define caching behavior for HTML vs static assets.

---

## File Content

```
# Force HTML to always revalidate (fresh pages)
# Applies to all HTML files
/*.html
  Cache-Control: no-cache, no-store, must-revalidate
  Pragma: no-cache
  Expires: 0

# Allow long caching for static assets (CSS, JS, images)
/assets/*
  Cache-Control: public, max-age=31536000, immutable

/images/*
  Cache-Control: public, max-age=31536000, immutable

```

---

## Breakdown

### HTML Pages
```plain
/*.html
  Cache-Control: no-cache, no-store, must-revalidate
  Pragma: no-cache
  Expires: 0
```
- `/*.html` → Applies rules to all HTML files.  
- `Cache-Control: no-cache, no-store, must-revalidate` → Forces browsers to always request the latest version of HTML pages (no caching).  
- `Pragma: no-cache` → Legacy HTTP/1.0 header for older clients.  
- `Expires: 0` → Explicitly sets expiry to the past, ensuring freshness.

👉 This guarantees users always see the newest HTML.

---

### Static Assets
```plain
/assets/*
  Cache-Control: public, max-age=31536000, immutable

/images/*
  Cache-Control: public, max-age=31536000, immutable
```
- Applies to CSS, JS, and image assets.  
- `public` → Allows caching by browsers and CDNs.  
- `max-age=31536000` → Cache assets for 1 year (31,536,000 seconds).  
- `immutable` → Tells browsers files will never change (safe if filenames are cache-busted, e.g., versioned).

👉 This speeds up load time and reduces bandwidth.

---

## Suggestions
- Make sure assets have versioned filenames (hash or unique name). Otherwise browsers may not fetch updates.  
- If using Netlify, confirm `_headers` is placed in the repo root (Netlify will detect it).  
- Optionally add `Content-Security-Policy` rules for stronger security.

---

**Reviewed for educational literacy by ChatGPT‑5.**
