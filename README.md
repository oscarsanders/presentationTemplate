# beamerthememinimalist

A minimalist, grayscale **Beamer theme** for technical talks and lectures.
White background, sans-serif text, no navigation symbols, and a small set of
reusable building blocks: one/two/three columns, process flows, tables, boxes
and code listings.

* Documentation and commands are in **English**.
* Slide *content* can be in **any `babel` language** (Spanish tested for
  encoding and accents: `ñ á é í ó ú ¿ ¡`).
* Works with **pdfLaTeX, XeLaTeX and LuaLaTeX** (engine detected via `iftex`).

Version 1.0.0 -- see `CHANGELOG.md`. License: MIT (see `LICENSE`).

## Files

| File | Purpose |
|------|---------|
| `beamerthememinimalist.sty` | The theme (the only file you need) |
| `minimalist-manual.tex/.pdf` | User manual and gallery; itself built with the theme |
| `example-spanish-session5.tex` | Complete 22-slide example in Spanish |
| `README.md`, `CHANGELOG.md`, `LICENSE` | Project metadata |

## Installation

Either keep `beamerthememinimalist.sty` next to your `.tex` file, or install it
once for all your documents:

```
$(kpsewhich -var-value TEXMFHOME)/tex/latex/beamer-minimalist/beamerthememinimalist.sty
```

(then run `texhash` if your distribution requires it).

Required packages (all in TeX Live / MiKTeX): `beamer`, `tikz`, `tcolorbox`,
`listings`, `booktabs`, `array`, `ragged2e`, `adjustbox`, `iftex`, `amsmath`,
`amssymb`, `pgf`; plus `psnfss` (pdfLaTeX) or `fontspec` + TeX Gyre Heros
(XeLaTeX/LuaLaTeX).

## Quick start

```latex
\documentclass[11pt,aspectratio=169]{beamer}
\usepackage[spanish,es-tabla]{babel}     % or english, etc. -- load BEFORE the theme
\usetheme[footer=total]{minimalist}

\title{My talk}
\author{Me}

\begin{document}
\begin{frame}\titlepage\end{frame}
\begin{frame}{Hello}
  Some text and a \concept{key term}.
\end{frame}
\end{document}
```

Compile with `latexmk -pdf file.tex` (or `-xelatex` / `-lualatex`).

## Theme options

`\usetheme[<options>]{minimalist}`

| Option | Values | Default | Effect |
|--------|--------|---------|--------|
| `accent` | any xcolor expression | `black!75` | Bullets, rules, box frames, titles |
| `footer` | `number`, `total`, `none` | `number` | Frame counter (bottom right) |
| `font` | `helvetica`, `default` | `helvetica` | Helvetica clone or Beamer's default sans |
| `titlerule` | boolean | `false` | Thin rule under each frame title |
| `sectionpages` | boolean | `false` | Divider frame at every `\section` |

## Columns (one, two or three)

By default a frame is a single full-width column. Use these where needed:

```latex
\begin{onecol}[width=0.7] ... \end{onecol}          % narrower, centered
\begin{twocol}[split=0.45,gap=0.04,align=T]
  left \nextcol right
\end{twocol}
\begin{threecol}[gap=0.06] A \nextcol B \nextcol C \end{threecol}
```

## Other building blocks

| Item | Description |
|------|-------------|
| `\concept{}`, `\code{}`, `\arr` | Bold term, monospace, right arrow |
| `\flowline{A, B, C}` | Inline `A -> B -> C` (bold) |
| `\flow[tikz opts]{A, B\\x, C}` | TikZ chain of nodes joined by arrows, auto-shrunk to the line width |
| TikZ styles | `mn node`, `mn arrow`, `mn dashed arrow`, `mn circle`, `mn flow` |
| `callout[opts]` | Outlined box; `title=...`, `halign=center`, any tcolorbox key |
| `statement[opts]` | Centered, emphasized box |
| `notebox[opts]` | Gray note with a left bar |
| Column types | `L{w}`, `C{w}`, `R{w}` for `tabular` (use with `booktabs`) |
| `lstlisting` | Style `minimalist` is active by default; frames need `[fragile]` |

Standard Beamer elements (`block`, `alertblock`, `exampleblock`, `theorem`,
`figure` + `\caption`, `\tableofcontents`) are restyled to match.

## Notes

* **Top alignment:** `\documentclass[t]{beamer}` (and `\begin{frame}[c]` for
  title/section slides). Default Beamer behavior is vertically centered.
* **Fragile frames:** a frame containing `lstlisting` must not contain the
  literal text `\end{frame}` inside the listing (Beamer limitation).
* **Spanish:** `es-tabla` makes captions read "Tabla"; add `es-noshorthands`
  if you hit conflicts with `<`/`>` in code.

## Versioning

Semantic Versioning 2.0.0. Public interface: theme options, environments,
commands and TikZ style names listed above.
