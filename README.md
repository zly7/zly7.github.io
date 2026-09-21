# zly7.github.io

Static portfolio site for `zly7`, rebuilt as a single-page public portfolio for internship applications and external technical presentation.

## Core File

- `index.html`: main site entry and the most important file to edit.

## Assets

- `public/assets/projects/`: retained legacy project images; the current minimalist homepage does not display image cards.
- `public/resume/zly7-resume.pdf`: current Chinese resume PDF.
- `public/resume/zly7-resume-en.pdf`: current English resume PDF; the homepage language toggle switches CV links automatically.

## Shared Codex Config

- `.codex/`: shareable Codex dangerous-permissions config for trusted Codex runs.
- Optional global install on Windows: `powershell -File .\.codex\install-windows.ps1`.

## Deploy To GitHub Pages

1. Push this repository to `main`.
2. Open repository `Settings`.
3. Enter `Pages`.
4. Choose `Deploy from a branch`.
5. Select branch `main` and folder `/ (root)`.
6. Save and wait for the site to publish.

Published URL:

- `https://zly7.github.io/`
