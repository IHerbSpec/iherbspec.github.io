# Editing the IHerbSpec Website and Protocol

This tutorial explains how the IHerbSpec website is organized and how to make edits to website pages and the IHerbSpec Protocol.

The goal is to provide enough functional knowledge to understand where content lives, how it is rendered into a website, and how to make and publish changes.

## How the website works

The IHerbSpec website is built using Quarto.

The source files are written in plain text using Quarto Markdown (`.qmd`) files. These source files are converted into HTML pages that are displayed on the public website.

The workflow is:

```text
.qmd files
      ↓
quarto render
      ↓
HTML files in docs/
      ↓
GitHub Pages website
```

In practice:

1. Edit a source file (`.qmd`, `.yml`, or `.css`).
2. Run:

```bash
quarto render
```

3. Review the changes by looking at your local HTML files
4. Go back to step 1, if necessary, or proceed if everything looks good.
5. Commit the changes using Git.
6. Push the changes to GitHub.
7. GitHub Pages automatically updates the website.

## Repository Organization

The https://github.com/IHerbSpec/iherbspec.github.io repository contains both the source files and the rendered website files.

```text
iherbspec.github.io/
├── _quarto.yml
├── styles.css
├── index.qmd
├── about.qmd
├── people.qmd
├── publications.qmd
├── contact.qmd
├── protocol.qmd
├── protocol/
├── images/
└── docs/
```

### Source files

Most website content is stored in `.qmd` files.

Examples:

```text
index.qmd
publications.qmd
contact.qmd
protocol/part4-metadata.qmd
```

These are the files you will edit most often.

### Rendered website

The rendered HTML files are stored in:

```text
docs/
```

These files are generated automatically by Quarto using `quarto render` in the command line.

In general, you should edit the source files rather than the HTML files.

## Main Website Pages

The main website pages live in the repository root:

```text
index.qmd
about.qmd
people.qmd
publications.qmd
contact.qmd
```

These generate pages such as:

```text
https://iherbspec.github.io/
https://iherbspec.github.io/publications.html
https://iherbspec.github.io/contact.html
```

## The Protocol

The protocol is organized as a separate Quarto book within:

```text
protocol/
```

The major sections of the protocol are stored as separate files:

```text
protocol/
├── preface.qmd
├── part1-overview.qmd
├── part2-workflow.qmd
├── part3-filenames.qmd
├── part4-metadata.qmd
├── part5-instrumentation.qmd
├── part6-guidelines.qmd
├── appendix1.qmd
├── appendix2.qmd
└── references.qmd
```

Each file corresponds to a major section of the protocol.

## Types of Files

Three file types are commonly edited.

### QMD Files

QMD files contain most website and protocol content.

Examples:

```text
publications.qmd
contact.qmd
protocol/part4-metadata.qmd
```

QMD files contain:

- text
- headings
- tables
- figures
- links
- citations
- cross-references

Most edits will be made in QMD files.

### YAML Files

YAML controls page settings and website structure.

You will see YAML at the top of many QMD files:

```yaml
---
title: "Publications"
---
```

YAML is also used in configuration files such as:

```text
_quarto.yml
protocol/_quarto.yml
```

These files control:

- navigation menus
- page order
- rendering options
- website configuration

Important:

> YAML is sensitive to indentation. Be careful when editing spaces.

### CSS Files

CSS controls the visual appearance of the website.

The main CSS file is:

```text
styles.css
```

CSS controls:

- fonts
- colors
- spacing
- layout
- page appearance

It does not control the Protocol pdf.

Edit CSS only when changing the appearance of the website.

## Common Editing Tasks

### Updating Website Text

Edit the appropriate QMD file.

Examples:

| Page | File |
|--------|--------|
| Homepage | `index.qmd` |
| Publications | `publications.qmd` |
| Contact | `contact.qmd` |
| People | `people.qmd` |

### Updating Protocol Text

Edit the appropriate protocol section.

Examples:

| Protocol Section | File |
|--------|--------|
| Part 1 | `protocol/part1-overview.qmd` |
| Part 2 | `protocol/part2-workflow.qmd` |
| Part 3 | `protocol/part3-filenames.qmd` |
| Part 4 | `protocol/part4-metadata.qmd` |
| Part 5 | `protocol/part5-instrumentation.qmd` |
| Part 6 | `protocol/part6-guidelines.qmd` |

### Updating Images

Website images are typically stored in:

```text
images/
```

Protocol images are typically stored in:

```text
protocol/images/
```

### Updating Navigation Menus

Main website navigation is controlled by:

```text
_quarto.yml
```

Protocol navigation is controlled by:

```text
protocol/_quarto.yml
```

### Updating Website Appearance

Edit:

```text
styles.css
```

## Quick Reference

| If you want to change... | Edit this file |
|-------------------------|---------------|
| Homepage | `index.qmd` |
| Publications page | `publications.qmd` |
| Contact page | `contact.qmd` |
| People page | `people.qmd` |
| Protocol landing page | `protocol.qmd` |
| Protocol Part 1 | `protocol/part1-overview.qmd` |
| Protocol Part 2 | `protocol/part2-workflow.qmd` |
| Protocol Part 3 | `protocol/part3-filenames.qmd` |
| Protocol Part 4 | `protocol/part4-metadata.qmd` |
| Protocol Part 5 | `protocol/part5-instrumentation.qmd` |
| Protocol Part 6 | `protocol/part6-guidelines.qmd` |
| Website navigation | `_quarto.yml` |
| Protocol navigation | `protocol/_quarto.yml` |
| Website appearance | `styles.css` |

## Rendering the Website

After making edits, update the website output by running:

```bash
quarto render
```

This command rebuilds the website and updates the HTML files stored in:

```text
docs/
```

Check for errors before proceeding.

## Publishing Changes

After rendering:

```bash
git status
git add .
git commit -m "Describe the changes"
git push
```

The updated website will be published automatically through GitHub Pages.

Note: This workflow assumes you have write access to the IHerbSpec repository and are permitted to push directly to the `main` branch.