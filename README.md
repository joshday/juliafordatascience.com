# Julia for Data Science

Source for [juliafordatascience.com](http://juliafordatascience.com) — a blog about using Julia for data science, statistics, and scientific computing.

Built with [Quarto](https://quarto.org) and deployed to GitHub Pages via GitHub Actions.

## Local Development

**Prerequisites:** [Quarto](https://quarto.org/docs/get-started/) and [Julia](https://julialang.org/downloads/)

```bash
# Install Julia dependencies
julia --project=. -e 'using Pkg; Pkg.instantiate()'

# Preview the site (live reload)
quarto preview

# Render the full site
quarto render
```

Posts that execute Julia code have their own `Project.toml` in their subdirectory. The CI workflow installs all of them automatically.

## Structure

```
posts/
  from_ghost/      # Posts migrated from the original Ghost site
  heyjoshday.com/  # Posts migrated from heyjoshday.com
  2025/            # New posts
```

## Contributing

Contributions are welcome — open an issue or pull request on [GitHub](https://github.com/joshday/juliafordatascience.com).
