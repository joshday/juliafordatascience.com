# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Quarto-based static blog at [juliafordatascience.com](https://juliafordatascience.com), deployed to GitHub Pages via GitHub Actions. Content is written in `.qmd` (Quarto Markdown) files with Julia code execution.

## Commands

```bash
# Install Julia dependencies (root project)
julia --project=. -e 'using Pkg; Pkg.instantiate()'

# Preview site locally with live reload
quarto preview

# Full render (produces _site/)
quarto render
```

## Architecture

- **`_quarto.yml`** — Site-wide configuration (theme, navbar, format settings)
- **`posts/`** — Blog posts organized in three subdirectories:
  - `from_ghost/` — Posts migrated from Ghost platform
  - `heyjoshday.com/` — Posts migrated from heyjoshday.com
  - `2025/` (and future year dirs) — New posts
- **`assets/`** — CSS, HTML templates, and images
- **`_freeze/`** — Cached Quarto execution outputs (committed to repo; only re-rendered when source changes)
- **`_site/`** — Build artifact (gitignored)

## Post Structure

Each post is a directory under `posts/` containing an `index.qmd` with YAML frontmatter. Posts with Julia code have their own `Project.toml` (and optionally `Manifest.toml`) for reproducibility. The CI pipeline automatically finds and instantiates all `Project.toml` files in the repo.

## Freeze Behavior

`posts/_metadata.yml` sets `freeze: auto` — Quarto only re-executes Julia code when source files change. Frozen outputs are stored in `_freeze/` and committed to git. To force re-execution of a specific post, delete its entry in `_freeze/`.

## Deployment

Push to `main` triggers `.github/workflows/Publish.yml`, which renders and publishes to the `gh-pages` branch automatically.
