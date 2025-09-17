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

Example (commit:  
[45b589a5f3c85130da4cab762ea2ae77fcdfa02c](https://github.com/ixventure/index_main/tree/45b589a5f3c85130da4cab762ea2ae77fcdfa02c)):

```
index_main-rollback-cf64385/
├── index.md
├── projects.md
├── _projects/
│   ├── project-a.md
│   ├── project-b.md
│   ├── test.md
│   └── dom.md   (maps all reviews together)
├── assets/
│   └── css/style.scss
├── CNAME
├── _config.yml
├── _headers
├── version.json
└── AI-generated *_review.md files
```

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
