# Simple Beamer deck

A small 16:9 LaTeX presentation with one consistent look: dark background, light text, one cyan accent, fixed margins, and page numbers. Start a new deck by editing `main.tex`; leave shared styling and image lookup in `preamble.tex`.

## Slide rhythm

- Give each slide one clear title.
- Add one short `\Takeaway{...}` when the slide has a main point.
- Use one simple arrangement for the evidence: text, columns, a table, a chart, or a figure.
- Add `\Source{...}` when a slide uses external evidence.
- Keep the palette and spacing consistent. Avoid adding decorative elements just to fill space.

The example slide in `main.tex` shows the default title, takeaway, two-column, and source treatments. Copy its frame when adding a slide.

## Figures

Put source images in `figures/`. PNG and PDF files in that folder are tracked by Git and can be pushed to Overleaf with the rest of the project. LaTeX searches this folder automatically, so either extension works:

```tex
\includegraphics[width=0.82\linewidth]{rotation-curve.pdf}
```

Prefer PDF for vector figures and PNG for raster images. Keep the original figure files here rather than only embedding them in the compiled deck.

## Build

With a LaTeX installation that includes Beamer:

```sh
latexmk -pdf -outdir=build main.tex
```

The generated PDF and temporary build files stay out of Git.

## Sync local files, GitHub, and Overleaf

The working directory is the Git repository. Commit source and figures as usual, then push to GitHub:

```sh
git add main.tex preamble.tex README.md figures
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
