# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

LaTeX CV/resume repository for Gabriel Ramirez. Contains English (`cv_11.tex`) and Spanish (`cv_11-sp.tex`) versions of a professional CV, compiled to PDF via LaTeX.

## Build Commands

```bash
# Compile English CV
pdflatex cv_11.tex

# Compile Spanish CV
pdflatex cv_11-sp.tex
```

Requires a LaTeX distribution (e.g., TeX Live, MiKTeX) with `pdflatex` available.

## CI/CD

GitHub Actions (`.github/workflows/build-latex.yml`) automatically compiles `cv_11.tex` to PDF on pushes/PRs to `master` and commits the resulting `cv_11.pdf` back to the repo. The Spanish version is **not** included in the CI pipeline.

## Architecture

- `structure.tex` — Shared LaTeX preamble, styling commands, and custom environments for the English CV
- `structure-sp.tex` — Spanish variant of the structure file (adds `babel` Spanish language support)
- `cv_11.tex` — English CV content; imports `structure.tex` via `\input`
- `cv_11-sp.tex` — Spanish CV content; imports `structure-sp.tex` via `\input`

The structure files define all custom commands (e.g., section formatting, entry layouts) that the content files use. When modifying styling, edit the `structure*.tex` files. When modifying CV content, edit the `cv_11*.tex` files.
