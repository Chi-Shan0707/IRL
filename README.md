# A Gentle Introduction to Inverse Reinforcement Learning — LaTeX source

This is a LaTeX reconstruction of the handout *"A Gentle Introduction to
Inverse Reinforcement Learning: What Must Be Assumed, and What Must Be
Approximated"* (Yuhan Chi, Fudan University, August 19, 2026).

## Files

- `main.tex` — the complete document. Self-contained: no external `.bib`
  file or image assets are needed (the bibliography is embedded via
  `thebibliography`, and there are no figures).
- `main.pdf` — a pre-compiled copy, included for convenience.

## Teaching companions (HTML)

Two self-contained teaching deliverables were built from `main.tex`.
They need no build step — just open them in a browser:

- **`irl-zh.html`** — a Chinese (Simplified), deliberately minimalist
  ("简约") long-form tutorial. The early material (forward RL, the
  ill-posedness of the inverse problem) is kept concise; everything
  **after maximum-entropy IRL** — the partition function, the worked
  example, maximum causal entropy, the three exits, occupancy measures,
  GAIL and AIRL — is derived one small step at a time. Eight interactive
  "显示下一步" derivation blocks (27 step cards in total) stage the
  load-bearing proofs (the MaxEnt optimiser, ∇log Z = E[Φ], the
  two-pass algorithm, the AIRL discriminator posterior, the
  entropy-as-a-function-of-ρ identity, and the guided-cost-learning weight
  cancellation); all steps remain visible if JavaScript is unavailable.
  A hand-calculation table in the GAIL section lets the reader verify the
  density-ratio claim with pencil and paper, an inline SVG diagram shows
  the two-pass backward/forward propagation, a 17-entry bibliography
  (`#refs`) records every attribution, and a reading-progress bar tracks
  position through the article.
- **`irl-slides.html`** — an English presentation deck (86 slides) for
  teaching IRL. The first half moves briskly; from the maximum-entropy
  algorithm onward the pace deliberately slows to one idea per slide
  with staged step-reveals. Includes presenter notes (`N`), an agenda /
  jump-grid (`O` or `Esc`), a talk timer (`T`), fullscreen (`F`), and arrow /
  space / Home / End navigation. The current slide is reflected in the URL
  hash, so links and refreshes return you to the same slide. The deck also
  degrades gracefully: a `<noscript>` stylesheet stacks all 86 slides with
  their staged reveals already open, and a print stylesheet produces a
  readable handout.
- **`assets/katex/`** — a vendored copy of KaTeX 0.16.9 (JS, CSS and the
  woff2 fonts). Both HTML files use it for mathematics, so **they render
  correctly with no internet connection**.

### Quick preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000/irl-zh.html
```

(Not strictly required — `file://` works too — but a local server avoids
any browser restrictions on vendored fonts.)

## How to compile

You need a standard TeX Live / MiKTeX installation with `pdflatex` and the
following packages (all part of any reasonably complete TeX Live install):
`amsmath`, `amssymb`, `amsfonts`, `mathtools`, `amsthm`, `booktabs`,
`array`, `enumitem`, `longtable`, `multirow`, `xcolor`, `tcolorbox`
(with the `most` bundle, which pulls in `breakable`/`skins`),
`algorithm`, `algpseudocode`, `hyperref`, `geometry`.

Compile with three passes of `pdflatex` (needed so that the table of
contents, cross-references, and section numbers all resolve — there is no
separate bibliography-compilation step since the references are embedded
directly):

```bash
pdflatex main.tex
pdflatex main.tex
pdflatex main.tex
```

Or, if you have `latexmk`:

```bash
latexmk -pdf main.tex
```

## Notes on this reconstruction

- The content, theorem/definition/example numbering, equation numbering,
  algorithms, tables, and the 23-item reference list were reproduced to
  match the original page-for-page as closely as ordinary `article`-class
  typesetting allows (37 pages here vs. 38 in the original — the
  difference is just incidental line/page breaking, not missing content).
- I checked every derivation, theorem statement, and the worked numerical
  example (Example 5.10) against the underlying mathematics. Everything
  checks out — including the subtle points the notes themselves are built
  around (the dynamics-induced reference measure in the maximum-entropy
  objective, the naive-vs-causal-entropy distinction, GAIL's discriminator
  carrying no reward information at convergence, and AIRL's state-only
  reward requirement). I did not find anything mathematically incorrect
  that needed fixing.
- Colour boxes (`graybox`, `redbox`, `navybox`/`navyplain`) are implemented
  as custom `tcolorbox` environments defined near the top of `main.tex`,
  and are easy to restyle (change the colours in the `Colours` section) if
  you want a different palette.
