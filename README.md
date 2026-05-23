# object-oriented-programming

Quarto-based study site for the C++ object-oriented programming final exam.

The site has one source of truth for each chapter:

- `notes/*.qmd` renders to HTML pages and per-chapter PDFs.
- `notes/_cram/*.qmd` stores the cram blocks included by both chapter pages and `cheat-sheet.qmd`.
- `slides/` can store original PDFs locally for cross-checking drafts, but it is ignored and not deployed.

## Local prerequisites

Install Quarto and a TeX distribution with XeLaTeX.

On WSL/Linux:

```bash
quarto install tinytex
sudo apt-get install fonts-noto-core fonts-noto-mono
```

On macOS:

```bash
brew install --cask quarto mactex-no-gui
```

## Preview and build

Run a live HTML preview:

```bash
quarto preview
```

Render the full site:

```bash
quarto render
```

Render a single chapter PDF:

```bash
quarto render notes/03-lop-doi-tuong.qmd --to pdf
```

Render all chapter PDFs:

```bash
for f in notes/0[0-7]-*.qmd; do quarto render "$f" --to pdf; done
```

Rendered output is written to `_site/` and is ignored by Git.

## Source PDFs

Original lecture and practice PDFs are not published with the site. Keep them locally in `slides/` if you need to cross-check or refine the AI-drafted notes. The directory is ignored by Git and is not listed as a Quarto resource.

## GitHub Pages

The workflow in `.github/workflows/pages.yml` installs Quarto and TinyTeX, renders the project, uploads `_site/`, and deploys it to GitHub Pages.

To publish:

1. Push to `main`.
2. In GitHub, set `Settings` > `Pages` > `Build and deployment` > `Source` to `GitHub Actions`.
3. Wait for the `Deploy GitHub Pages` workflow to complete.
