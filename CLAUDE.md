# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio and resume repository for Iván Moreno (SRE/DevSecOps Engineer). The core artifact is a LaTeX-based CV compiled to PDF and distributed via GitHub Releases.

## Build Commands

All build commands run from the `curriculumVitae/` directory:

```bash
cd curriculumVitae

make all          # Compile cv_en.pdf
make en           # Same as make all
make patch-date   # Stamp the CV with the current date
make clean        # Remove LaTeX auxiliary files (not the PDF)
make view         # Open compiled PDF with okular
```

CI builds using: `make patch-date && make all`

## CI/CD Pipeline

Defined in `.github/workflows/buldCV.yml`:
- Triggers on push to `master` and on version tags (`v*`)
- Installs TexLive: `texlive-fonts-extra`, `texlive-latex-extra`, `texlive-lang-spanish`
- Uploads artifact as `Resume_Ivan_Moreno`
- On tagged releases, attaches the PDF as `Resume_Ivan_Moreno.pdf`

To publish a new release, push a version tag (e.g., `git tag v1.x && git push origin v1.x`).

## CV Source

`curriculumVitae/cv_en.tex` — single-file LaTeX document using the `article` class with:
- A4 paper, 1.8cm margins
- Packages: `fontenc`, `inputenc`, `geometry`, `hyperref`, `enumitem`, `parskip`, `titlesec`, `array`, `xcolor`
- LinkedIn blue (`#0A66C2`) as the link color

The `.gitignore` excludes all LaTeX auxiliary files and compiled PDFs, so only `.tex` source is tracked.
