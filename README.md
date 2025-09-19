# IxVentures Jekyll DOM Template

This repository contains the **IxVentures Jekyll DOM Template**, a
GitHub-hosted **Document Object Model (DOM) architecture**.
It is both a **technical framework** and a **digital legal formalism object** —
designed to encode structure, accountability, and reproducibility in digital projects.

---

## Purpose

DOMs are not only browser artifacts.
At IxVentures, we treat DOMs as **formal digital objects**, capable of carrying
**legal, technical, and governance meaning**.

This template:

* Uses **Jekyll** to transform structured markdown into static, auditable DOM artifacts.
* Provides a **mapping of repository files** alongside AI-generated reviews.
* Demonstrates how a **repo → framework → DOM** workflow can establish
  transparency, reproducibility, and machine-human accountability.

---

## Project Context

This template has been created for the
[x.com/nocap\_so](https://x.com/nocap_so) **90-day sprint**, in collaboration with

* [github.com/bestape/neowise](https://github.com/bestape/neowise)
* The world’s first **"AIpreneur" DAO** — a serial solo entrepreneur teaching a
  **1 perfect pupil business model**.

---

## Features

* **Markdown-Driven**: All project docs and reviews are structured in `.md`.
* **AI-Reviewed Files**: Each source file has an accompanying `*_review.md`.
* **File Mapping**: A `dom.md` project maps the repository structure in human-readable form.
* **Version Tracking**: `version.json` ensures reproducibility by commit.
* **GitHub Integration**: Designed for GitHub Pages (or any Jekyll host).

---

## Project Thumbnails & Gallery

The template automatically detects project thumbnail images:

* Any file in a project folder that matches `*-1.*` is used as the main thumbnail.
* Works with any extension (`png, jpg, jpeg, svg`, etc.).
* Falls back to `/assets/images/logo.png` if no image is found.

Example (home/projects listing):

```liquid
{%- assign project_files = site.static_files | where_exp: "f", "f.path contains project_path" | sort: "path" -%}
{%- assign found_thumb = "" -%}
{%- for f in project_files -%}
  {%- assign name = f.name | downcase -%}
  {%- assign parts = name | split: "-" -%}
  {%- if parts.size > 1 -%}
    {%- assign number_part = parts.last | split: "." | first -%}
    {%- if number_part == "1" -%}
      {%- assign found_thumb = f.path -%}
      {%- break -%}
    {%- endif -%}
  {%- endif -%}
{%- endfor -%}
```

---

## Repository Structure

Snapshot from commit
[45b589a5f3c85130da4cab762ea2ae77fcdfa02c](https://github.com/ixventure/index_main/tree/45b589a5f3c85130da4cab762ea2ae77fcdfa02c):

<details>
<summary>📑 Expand repository structure</summary>

```
index_main-rollback-cf64385/
├── CNAME
├── README.md
├── _config.yml
├── _includes/
│   └── gallery.html
├── _layouts/
│   ├── default.html
│   └── project.html
├── _projects/
│   ├── project-a.md
│   ├── project-b.md
│   └── test.md
├── assets/
│   ├── css/
│   │   └── style.scss
│   ├── images/
│   │   └── logo.png
│   └── projects/
│       ├── project-a/
│       │   ├── image-1.png
│       │   ├── image-2.png
│       │   └── image-3.png
│       └── project-b/
│           └── image-1.svg
├── index.md
├── projects.md
└── version.json
```

</details>

---

## File Review Links

<details>
<summary>📑 Expand file review links</summary>

* [gallery.html review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_includes/galleryHtml_github_copilot_review.md)
* [default.html review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_layouts/defaultHtml_github_copilot_review.md)
* [project.html review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_layouts/projectHtml_github_copilot_review.md)
* [project-a.md review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/project-aMd_chatGPT_5_review.md)
* [project-b.md review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/project-bMd_github_copilot_review.md)
* [test.md review](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/testMd_chatGPT_5_review.md)
* [style.scss review](https://github.com/ixventure/index_main/blob/rollback-cf64385/assets/css/styleScss_chatGPT_5_review.md)
* [version.json review](https://github.com/ixventure/index_main/blob/rollback-cf64385/versionjson_chatGPT_5_review.md)

</details>

---

## How to Use

<details>
<summary>📑 Run your own site using this template on GitHub</summary>

1. Clone your fork:

```bash
git clone https://github.com/USERNAME/ixv-jekyll-minima-template.git
cd ixv-jekyll-minima-template
```

(Optional) Check out a specific commit if needed:

```bash
git checkout COMMIT-HASH
```

2. Repo URL mode (GitHub Pages):

* Delete `CNAME` if it exists.
* Update `_config.yml`:

```yaml
url: "https://USERNAME.github.io"
baseurl: "/ixv-jekyll-minima-template"
```

3. Optional: Custom domain via CNAME:

* Keep a `CNAME` file containing your domain.
* GitHub Pages serves site at that domain; no `_config.yml` changes needed.

4. Local preview:

```bash
bundle exec jekyll serve
```

5. Deploy:

* Push changes to GitHub.
* `version.json` tracks builds and triggers update notifications.

*Replace `USERNAME` and `COMMIT-HASH` with your GitHub username and the commit hash if needed.*

</details>

---

## Strengths

* **Simplicity**: Minimal markdown + YAML → reproducible DOM.
* **Auditability**: Every file has an AI-reviewed mirror.
* **Transparency**: Repo, configs, and generated site are visible.
* **Community Support**: Built on Jekyll + GitHub Pages ecosystem.

---

## Limitations

* **Indirect DOM Generation**: Output via Jekyll build, not raw repo.
* **Loss of Fidelity**: Non-rendered files (branches, comments, binaries) not fully captured.
* **Dependency**: DOM integrity depends on Jekyll + configuration stability.

---

## License

© IxVentures Studio.
Open for experimental use under permissive terms.
See `LICENSE` for details.

---

## Acknowledgments

* Sprint partner: [@nocap\_so](https://x.com/nocap_so)
* DAO partner: [bestape/neowise](https://github.com/bestape/neowise)
* AI review contributions: ChatGPT 5, GitHub Copilot
