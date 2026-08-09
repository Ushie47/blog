---
title: "CI/CD with GitHub Actions"
date: 2026-08-09
draft: false
---

Continuous Integration and Continuous Deployment (CI/CD) automate the
process of building, testing, and publishing software whenever changes
are pushed to a repository. This project uses GitHub Actions to
automatically build and deploy the site to GitHub Pages on every push
to the `main` branch.

## How the workflow works

The workflow file (`.github/workflows/hugo.yml`) defines a job that:

1. Checks out the repository, including Git submodules (the theme)
2. Installs the correct Hugo version
3. Runs `hugo --minify` to build the static site
4. Uploads the built site as a Pages artifact
5. Deploys that artifact to GitHub Pages

## Why this matters

Without CI/CD, publishing a change would mean manually building the
site locally and uploading the output somewhere. With this pipeline,
every `git push` automatically results in a live update — the exact
process used throughout this project, from Stage 1 onward.

## Lessons learned

Working with this pipeline surfaced real issues: submodules needing
`submodules: recursive` in the checkout step, workflow permissions
needing to allow writing to Pages, and even a GitHub-wide infrastructure
outage affecting Actions and Pages simultaneously — a good reminder that
automation still depends on external infrastructure being available.
