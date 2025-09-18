# Line-by-line explanation of `project-b.md`

This file is a Jekyll project page written in Markdown with YAML front matter.

## Source

```markdown
---
title: Project B
slug: project-b
layout: project
description: This is where the project description should go!
---

This is **Project B**, another example project.

Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin.

- Benefit 1
- Benefit 2
- Benefit 3

```

## Line-by-line explanation

### 1

```
---
```
Start of the YAML front matter block. Everything between the opening and closing `---` is metadata.

### 2

```
title: Project B
```
YAML key `title` sets the page title to 'Project B'. This is used in layouts and navigation.

### 3

```
slug: project-b
```
YAML key `slug` defines the unique identifier 'project-b'. Useful for URLs and includes.

### 4

```
layout: project
```
YAML key `layout` specifies the layout template to use. Here it uses the `project` layout.

### 5

```
description: This is where the project description should go!
```
YAML key `description` provides a human-readable description of the project. Shown in listings or metadata.

### 6

```
---
```
End of the YAML front matter block. After this, normal Markdown content begins.

### 7

```
(blank line)
```
Blank line, separates sections in Markdown.

### 8

```
This is **Project B**, another example project.
```
Markdown paragraph introducing Project B. Uses `**` around 'Project B' to bold it.

### 9

```
(blank line)
```
Blank line, separates sections in Markdown.

### 10

```
Cras sit amet nibh libero, in gravida nulla. Nulla vel metus scelerisque ante sollicitudin.
```
Another Markdown paragraph with placeholder (Lorem Ipsum–style) filler text.

### 11

```
(blank line)
```
Blank line, separates sections in Markdown.

### 12

```
- Benefit 1
```
Markdown list item showing a project benefit. Rendered as a bullet point in HTML.

### 13

```
- Benefit 2
```
Markdown list item showing a project benefit. Rendered as a bullet point in HTML.

### 14

```
- Benefit 3
```
Markdown list item showing a project benefit. Rendered as a bullet point in HTML.
