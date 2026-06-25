# When Forgiveness Backfires: Rejection Sensitivity and Cooperative Behavior Following Exposure to Adaptive Forgiving Agents

This repository contains the data, analysis code, and manuscript for a study investigating whether exposure to forgiving artificial agents improves cooperative behavior in trust games, and how rejection sensitivity (RS) moderates this effect.

## Overview

In a randomized controlled online experiment, 206 participants pre-screened for high or low rejection sensitivity played repeated trust games (RTGs) against Hidden Markov Model (HMM)-based artificial investors. Participants were randomly assigned to interact with either forgiving HMM agents (Manipulation) or standard human-like HMM agents (Control) during an exposure phase, before playing a final trust game. Contrary to expectations, exposure to forgiving agents led to *reduced* cooperation, potentially driven by negative contrast effects.

## Repository Structure

```
.
├── article_anon.Rmd     # Main manuscript with all embedded statistical analyses
├── supplement.Rmd       # Supplementary information (model specifications, tables)
├── bib/
│   └── exposure.bib     # Bibliography (BibTeX)
├── apa.csl              # APA citation style
├── data/
│   ├── d_finished.RData # Main experimental dataset (206 participants, trust game data)
│   ├── longFormData.csv # HMM training data (independent investor behavior dataset)
│   ├── trans_prob_all.RDS# HMM transition probabilities
│   └── mod_*.RDS        # Cached statistical model objects (for faster rendering)
└── figures/             # Static figures (HMM diagrams, experiment timeline)
```

## Reproducing the Analysis

### Requirements

- **R** (developed with R 4.5.1)
- **LaTeX** distribution (e.g., TinyTeX or TeX Live) for PDF rendering

### Key R Packages

```r
install.packages(c(
  "papaja", "bookdown", "tidyverse", "afex", "emmeans",
  "lsmeans", "depmixS4", "kableExtra", "flextable",
  "ggplot2", "gridExtra", "ggsignif", "magick", "patchwork",
  "lmerTest", "sjstats", "effectsize", "forcats"
))
```

### Rendering

To render the main manuscript:

```r
rmarkdown::render("article_anon.Rmd")
```

To render the supplementary information:

```r
rmarkdown::render("supplement.Rmd")
```

Note: The first render may take several minutes as statistical models are fitted. Subsequent renders use cached model objects in `data/mod_*.RDS`.

## Data Description

- **`d_finished.RData`**: The main analysis dataset containing trial-level trust game data for 206 participants across all experimental phases. Key variables include `condition.f` (Control/Manipulation), `high_RS` (low RS/high RS group), `gameNum.f` (game phase), `investment`, `returns`, and `investorState` (latent HMM state).

- **`longFormData.csv`**: Independent behavioral dataset of 381 human investors in 10-round trust games, used to train the HMM artificial investor agent.

## License

This project is shared for academic review and reproducibility purposes.
