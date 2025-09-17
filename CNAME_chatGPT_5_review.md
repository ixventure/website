# Line-by-Line Review of `CNAME`

**File Purpose:**  
The `CNAME` file tells GitHub Pages which **custom domain** to use for this site.

---

## File Content

```
ixventure.studio
```

### Explanation
- `ixventure.studio` → This is the custom domain configured for the site.  
- When this file is present in the repo root, GitHub Pages automatically maps the site from `ixventure.github.io/index_main` (the default) to **ixventure.studio**.

---

## Key Points
- **One line only** → must contain exactly the custom domain, nothing else.  
- **No extra whitespace** → no trailing spaces or newlines, or GitHub Pages may misinterpret it.  
- This integrates with your registrar/DNS (Cloudflare in your case) by pointing the domain’s DNS records to GitHub Pages IPs.

---

## Suggestions
- Verify that DNS A records (185.199.108.153–185.199.111.153) are set at Cloudflare.  
- Make sure Cloudflare SSL/TLS mode is set correctly to avoid 526 errors.  
- Keep this file at the repo root; moving or renaming it will break custom domain mapping.

---

**Reviewed for educational literacy by ChatGPT‑5.**
