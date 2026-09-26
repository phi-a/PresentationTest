# Simple Beamer deck

A small 16:9 LaTeX presentation based on `docs/research-template.pptx`. It uses a white background, Calibri text, Illinois blue (`#004C97`) titles and divider rules, dark gray body text, and Fermilab and DarkNESS logos. The Illinois Block I logo is omitted. `main.tex` sets up the deck and includes each slide in order. Keep shared styling and image lookup in `preamble.tex`.

The title slide uses a 40 pt blue title, 20 pt subtitle, and 14 pt gray author line. Content slides use a 24 pt blue title and 18 pt body. The divider rules and page numbers are blue.

## Slide files

Each slide lives in its own `.tex` file under `slides/`. Use a two-digit order number followed by a short lowercase name, such as `01-title.tex` or `02-dark-matter.tex`. The number gives the intended position in the deck.

Add each new slide to `main.tex` with an `\input{slides/...}` line in the same numbered order. The include list is the authoritative deck order. For example:

```tex
\input{slides/01-title}
\input{slides/02-dark-matter}
\input{slides/03-results}
```

To insert or move a slide, rename the affected files and update the include list. Keep each file to one `frame` environment; do not put the document preamble or `\begin{document}` in slide files.

## Slide rhythm

- Give each content slide one clear title.
- Use direct, left-aligned body text. Use bullets when listing points.
- Add `\Source{...}` when a slide uses external evidence.
- Keep the master logos, blue divider rules, and spacing consistent.

The example files show the title and content layouts. Copy a slide file when adding a slide.

## Figures

Put source images in `figures/`. PNG and PDF files in that folder are tracked by Git and can be pushed to Overleaf with the rest of the project. LaTeX searches this folder automatically, so either extension works:

```tex
\includegraphics[width=0.82\linewidth]{rotation-curve.pdf}
```

Prefer PDF for vector figures and PNG for raster images. Keep the original figure files here rather than only embedding them in the compiled deck.

## Build

Compile with XeLaTeX so the template can use system fonts:

```sh
latexmk -xelatex -outdir=build main.tex
```

Calibri is used when installed. If the compiler cannot find Calibri, the template falls back to Noto Sans so the deck still builds. The generated PDF and temporary build files stay out of Git.

## Sync local files, GitHub, and Overleaf

The working directory is the Git repository. Commit source and figures as usual, then push to GitHub:

```sh
git add main.tex preamble.tex README.md figures slides
git commit -m "Update presentation"
git push origin main
```

To connect this repository to an Overleaf project, copy that project's Git URL from Overleaf's **Menu → Git** panel, then add it once as a second remote:

```sh
git remote add overleaf <Overleaf-Git-URL>
```

After committing, send the current local `main` branch to Overleaf's `master` branch:

```sh
git push overleaf main:master
```

Push separately to `origin` and `overleaf`; Git does not automatically sync one remote to another. Before pushing, pull and resolve any edits made in Overleaf so its changes are not overwritten. Overleaf Git access requires an enabled Git integration and token-based authentication. See [Overleaf Git integration](https://www.overleaf.com/learn/how-to/Git_integration) and [authentication tokens](https://www.overleaf.com/learn/how-to/Git_integration_authentication_tokens).
