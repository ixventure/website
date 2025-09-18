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

- Uses **Jekyll** to transform structured markdown into static, auditable DOM artifacts.  
- Provides a **mapping of repository files** alongside AI-generated reviews.  
- Demonstrates how a **repo → framework → DOM** workflow can establish  
  transparency, reproducibility, and machine-human accountability.  

---

## Project Context

This template has been created for the  
[x.com/nocap_so](https://x.com/nocap_so) **90-day sprint**, in collaboration with  

- [github.com/bestape/neowise](https://github.com/bestape/neowise)  
- The world’s first **"AIpreneur" DAO** — a serial solo entrepreneur teaching a  
  **1 perfect pupil business model**.  

---

## Features

- **Markdown-Driven**: All project docs and reviews are structured in `.md`.  
- **AI-Reviewed Files**: Each source file has an accompanying `*_review.md`.  
- **File Mapping**: A `dom.md` project maps the repository structure in human-readable form.  
- **Version Tracking**: `version.json` ensures reproducibility by commit.  
- **GitHub Integration**: Designed for GitHub Pages (or any Jekyll host).  

---

## Repository Structure

This project snapshot is based on commit  
[45b589a5f3c85130da4cab762ea2ae77fcdfa02c](https://github.com/ixventure/index_main/tree/45b589a5f3c85130da4cab762ea2ae77fcdfa02c)

This project collected AI-generated review explanations for the repository files for this commit. The are included in the snapshot and listed below as *_review.md.

<details>
  <summary>📑 Click to expand repository structure</summary>

```
index_main-rollback-cf64385/
├── CNAME
├── CNAME_chatGPT_5_review.md
├── README.md
├── _config.yml
├── _config_chatGPT_5_review.md
├── _headers
├── _headers_chatGPT_5_review.md
├── _includes/
│   └── gallery.html
│       └── galleryHtml_github_copilot_review.md
├── _layouts/
│   ├── default.html
│   │   └── defaultHtml_github_copilot_review.md
│   └── project.html
│       └── projectHtml_github_copilot_review.md
├── _projects/
│   ├── project-a.md
│   │   └── project-aMd_chatGPT_5_review.md
│   ├── project-b.md
│   │   └── project-bMd_github_copilot_review.md
│   └── test.md
│       └── testMd_chatGPT_5_review.md
├── assets/
│   ├── css/
│   │   └── style.scss
│   │       └── styleScss_chatGPT_5_review.md
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
│   └── indexmd_chatGPT_5_review.md
├── projects.md
│   └── projectsmd_chatGPT_5_review.md
├── version.json
└── versionjson_chatGPT_5_review.md
```

</details>

---

## File Review Links

<details>
  <summary>📑 Click to expand file review links</summary>

- [galleryHtml_github_copilot_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_includes/galleryHtml_github_copilot_review.md) 
  *Handles the gallery include logic, generating dynamic image layouts.*

- [defaultHtml_github_copilot_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_layouts/defaultHtml_github_copilot_review.md)  
  *Defines the default layout template applied across pages.*

- [projectHtml_github_copilot_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_layouts/projectHtml_github_copilot_review.md) 
  *Provides the specialized layout for project detail pages.*

- [project-aMd_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/project-aMd_chatGPT_5_review.md) 
  *AI review of Project A’s markdown file.*

- [project-bMd_github_copilot_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/project-bMd_github_copilot_review.md)  
  *AI review of Project B’s markdown file.*

- [testMd_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_projects/testMd_chatGPT_5_review.md)  
  *AI review of the Test project markdown file.*

- [styleScss_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/assets/css/styleScss_chatGPT_5_review.md)  
  *Explains the SCSS stylesheet defining the site’s styles.*

- [CNAME_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/CNAME_chatGPT_5_review.md)  
  *Details the CNAME configuration for custom domain setup.*

- [_config_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_config_chatGPT_5_review.md) 
  *Breaks down the Jekyll site configuration YAML.*

- [_headers_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/_headers_chatGPT_5_review.md)
  *Covers Netlify/hosting header rules for performance and security.*

- [indexmd_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/indexmd_chatGPT_5_review.md)
  *Explains the site’s homepage markdown file.*

- [projectsmd_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/projectsmd_chatGPT_5_review.md)  
  *Explains the projects listing markdown file.*

- [versionjson_chatGPT_5_review.md](https://github.com/ixventure/index_main/blob/rollback-cf64385/versionjson_chatGPT_5_review.md) 
  *Details the version.json metadata file for version tracking.*

</details>
  
---

## How to Use

1. **Clone the repo**  
   ```bash
   git clone https://github.com/ixventure/index_main.git
   cd index_main
   ```

2. **Install Jekyll**  
   ```bash
   bundle install
   ```

3. **Run locally**  
   ```bash
   bundle exec jekyll serve
   ```

4. **Visit site**  
   Open [http://localhost:4000](http://localhost:4000)  

5. **Deploy to GitHub Pages**  
   - Push commits to your GitHub repo.  
   - Enable **Pages** in repo settings.  

---

## Strengths

- **Simplicity**: Minimal markdown + YAML → reproducible DOM.  
- **Auditability**: Every file has an AI-reviewed mirror for context.  
- **Transparency**: Repo, configs, and generated site are all visible.  
- **Community Support**: Built on Jekyll with GitHub ecosystem tools.  

---

## Limitations

- **Indirect DOM Generation**: Output is produced via Jekyll build, not raw repo.  
- **Loss of Fidelity**: Non-rendered files (branches, comments, binaries) not fully captured.  
- **Dependency**: DOM integrity depends on Jekyll + configuration staying stable.  

---

## License

© IxVentures Studio.  
Open for experimental use under permissive terms.  
See `LICENSE` for details.  

---

## Acknowledgments

- Sprint partner: [@nocap_so](https://x.com/nocap_so)  
- DAO partner: [bestape/neowise](https://github.com/bestape/neowise)  
- AI review contributions: ChatGPT 5, GitHub Copilot  
