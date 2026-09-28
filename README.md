# A Gentle Introduction to Inverse Reinforcement Learning

*What must be assumed, and what must be approximated.*

[![Website](https://img.shields.io/badge/website-chi--shan0707.github.io%2FIRL-2f5d9e)](https://chi-shan0707.github.io/IRL/)
[![Build notes](https://github.com/Chi-Shan0707/IRL/actions/workflows/build-notes.yml/badge.svg)](https://github.com/Chi-Shan0707/IRL/actions/workflows/build-notes.yml)

A derivation-first introduction to inverse reinforcement learning (IRL). It
starts from forward RL and ends at GAIL and AIRL. Three questions organise it:

1. **What can be inverted?** Demonstrations pin down a reward only up to a large
   equivalence class. What is the honest target?
2. **How do we choose within that class?** Maximum margin versus maximum
   (causal) entropy.
3. **What must be approximated once we leave the finite, tabular, known-dynamics
   world?** These are the three *exits*: infinite or continuous problems, learned
   features, and unknown dynamics.

**Read online → <https://chi-shan0707.github.io/IRL/>**

## Materials

| | Format | Description |
|---|---|---|
| [**Tutorial**](https://chi-shan0707.github.io/IRL/tutorial.html) | HTML | Long-form, blog-style walkthrough with interactive step-by-step derivations, a hand-checkable worked example, and light/dark mode. |
| [**Slides**](https://chi-shan0707.github.io/IRL/slides.html) | HTML | 86-slide lecture deck with staged reveals, presenter notes (`N`), overview grid (`O`), timer (`T`), and fullscreen (`F`). |
| [**Lecture notes**](https://chi-shan0707.github.io/IRL/irl-notes.pdf) | PDF | Typeset handout with definitions, theorems, proofs, algorithms, and references. Source: [`notes/irl-notes.tex`](notes/irl-notes.tex). |

## Contents

1. **Forward RL**: MDPs, policy evaluation as a linear solve, and Bellman
   optimality as a contraction fixed point
2. **The inverse problem**: the reward solution set is a polyhedral cone,
   potential shaping, and the choice of reward class
3. **Selection principles**: maximum margin (Abbeel & Ng, 2004) and maximum
   entropy (Ziebart et al., 2008), covering the partition function, a worked
   example, and maximum causal entropy
4. **Three exits**: (A) infinite horizons and continuous spaces, (B) learned
   features, (C) unknown dynamics
5. **Occupancy measures, GAIL, and AIRL**: imitation as density-ratio
   estimation, and recovering rewards that transfer
6. **Synthesis**: every method on two coordinates, a checklist for reading IRL
   papers, and common errors

## Repository layout

```
.
├── docs/                   # GitHub Pages site (served from /docs)
│   ├── index.html          # landing page
│   ├── tutorial.html       # long-form tutorial
│   ├── slides.html         # lecture deck
│   ├── irl-notes.pdf       # compiled lecture notes
│   └── assets/katex/       # vendored KaTeX 0.16.9 (works offline)
├── notes/
│   └── irl-notes.tex       # LaTeX source of the lecture notes
└── .github/workflows/      # CI: compiles the notes on every change
```

## Running locally

The site is static and needs no build step. KaTeX is vendored, so it also
works offline:

```bash
python3 -m http.server -d docs 8000   # open http://localhost:8000
```

Opening the HTML files directly (`file://`) also works.

## Building the notes

You need a TeX Live or MiKTeX installation with `pdflatex`:

```bash
cd notes
latexmk -pdf irl-notes.tex         # or run pdflatex irl-notes.tex three times
cp irl-notes.pdf ../docs/irl-notes.pdf
latexmk -c                         # clean up auxiliary files
```

The bibliography is embedded, so no BibTeX pass is needed. Required packages:
`amsmath`, `amssymb`, `mathtools`, `amsthm`, `booktabs`, `enumitem`,
`longtable`, `multirow`, `xcolor`, `tcolorbox` (`most`), `algorithm`,
`algpseudocode`, `hyperref`, and `geometry`.

## Citation

```bibtex
@misc{chi2026irl,
  author = {Chi, Yuhan},
  title  = {A Gentle Introduction to Inverse Reinforcement Learning:
            What Must Be Assumed, and What Must Be Approximated},
  year   = {2026},
  url    = {https://chi-shan0707.github.io/IRL/}
}
```
