# R for Social Scientists: Interactive Academy

An interactive, self-paced edition of Sofia Gil-Clavel's eleven-session course **R for Social Scientists**, rebuilt as a single-file learning academy. Every session keeps its original content and adds side-by-side Python translations, instant-feedback knowledge checks, browser-based coding labs in both R and Python, and applied exercises on synthetic health and social policy data: area deprivation, transport access, a community transport grant programme, and emergency hospital admissions.

It spans data frames and the tidyverse, visualisation, unsupervised and supervised learning, statistics, text as data, text mining, machine learning for text, programming and APIs, parallelisation, and building an R package.

![R for Social Scientists Academy: course snapshot](Course%20snapshot.png)

## Start the Interactive Academy

**[Open the interactive course](REPLACE-WITH-YOUR-GITHUB-PAGES-URL)**

The academy preserves the original course structure and adds an interactive learning layer:

- **13 chapters**: a course overview, the 11 original sessions and the extra session on building a package. Each has learning objectives from the original lesson plans, a summary of the original slides and scripts, and side-by-side R / tidyverse and Python / pandas examples.
- **13 applied chapter labs and 10 practicum labs**, editable and runnable in the browser in **either R (webR) or Python (Pyodide)**. Switch language per lab or set a default for the whole course. Internet access is required on first use to load each runtime and its packages.
- **13 knowledge checks** with immediate feedback and explanations, plus "check your understanding" questions with worked answers.
- **A Part II practicum** that walks through evaluating a community transport grant programme, from checking keys to publishing a disclosure-safe table, with 20 worked examples in each language.
- **A capstone**: first respiratory emergency admission by deprivation quintile, with a washout, censoring, person-time denominators and a rate ratio. The code checks its own results in both languages.
- **A cohort simulator, a searchable R ↔ Python reference (49 translations), a learning dashboard and progress tracking**, plus embedded datasets and downloadable companion scripts.

The course is distributed as **one self-contained `index.html` file**. Lessons, data and quizzes are embedded; only code execution needs the online runtimes. The companion R and Python scripts run every lab locally if you prefer RStudio, VS Code or Jupyter.

### How to use the course

1. **Learn:** read the summary of the original session and the learning objectives.
2. **Compare:** read the R and Python versions side by side, and the trap that changes results between them.
3. **Practise:** run the applied lab in R, switch to Python, and confirm you get the same answer.
4. **Apply:** work through the practicum labs and the capstone on the synthetic cohort.
5. **Check:** answer the knowledge check, attempt the practice challenge, and mark the chapter complete.

## Who This Is For

The original course was designed for academics at every career stage, from PhD students to professors, including qualitative researchers who have never used R and quantitative researchers moving from SPSS or Stata.

This edition also serves:

- **Analysts and evaluators in health and social policy** who want a method grounded in realistic data problems: deprivation gradients, missing follow-up, censoring, confounded programme comparisons and small-number suppression.
- **R users learning Python, and Python users learning R**, because every lab is written in both languages and gives the same result.

## What Makes This Edition Different

- **Two languages, one answer.** Every chapter lab, practicum example and the capstone was run in R and Python and produces the same numbers. Where results legitimately differ, the page says why.
- **Defaults that change results are named.** For example:

```text
R                                    Python                               Watch for
mean(x)                              s.mean()                             pandas skips NA by default; R returns NA
glm(y ~ x, family = binomial)        LogisticRegression()                 scikit-learn adds an L2 penalty by default
tidytext::bind_tf_idf()              TfidfVectorizer()                    different (smoothed) idf formula
prcomp(X, scale. = TRUE)             PCA() on StandardScaler()            component signs are arbitrary
set.seed(1)                          default_rng(1)                       different generators, different draws
left_join(..., relationship =        merge(..., validate=                 declare cardinality so duplicates raise
  "many-to-one")                       "many_to_one")
```

- **Applied, not toy, examples.** Labs ask the questions a real evaluation asks: what one row means, who is missing, how long each person was followed, and whether a comparison group differs before the programme started.

## What's Covered

| Block | Session | Topics |
| --- | --- | --- |
| **Foundations** | 0. How the course fits together | Course map, project setup with `renv` and `venv`, framing an analysis by population, exposure, outcome and time window |
| **Data handling** | 1. Data frames | Data types, vectors, indexing, reading and saving data, identifier types and leading zeros |
| | 2. Tidyverse | Packages, the dplyr verbs, the pipe, grouped summaries, missing-value defaults |
| **Exploratory analysis** | 3. Data visualisation | Grammar of graphics, geoms, scales, facets, themes, denominators on charts; ggplot2, plotnine and matplotlib |
| | 4. Unsupervised learning | Standardisation, PCA, variance explained, k-means, area typologies |
| **Machine learning** | 5. Statistics | Formula notation, `lm`, outliers, assumptions, confidence intervals, interactions, ANOVA, prediction, `glm`; statsmodels equivalents |
| | 6. Supervised learning | Logistic regression, LDA, train/test splits, cross-validation, majority-class baselines, leakage |
| **Text analysis** | 7. Text as data | stringr, encodings, tokenising, stop words, stemming, word frequencies |
| | 8. Text mining | tf-idf, n-grams, word correlations, networks, part-of-speech tagging |
| | 9. Machine learning for text | Text recipes, topic models, naive Bayes classification, resampled metrics |
| **Code optimisation** | 10. Basic programming | APIs with httr2 and requests, functions, conditions, loops, error handling, retries |
| | 11. Servers and parallelisation | Vectorisation, apply family, `future`, `foreach`, joblib, bootstrap timing, reproducible parallel seeds |
| **Extra** | A. Building a package | DESCRIPTION, roxygen2, testthat, devtools; `pyproject.toml` and pytest |

## Part II Practicum: Evaluating a Community Transport Grant Programme

The practicum follows one evaluation from raw tables to a publishable result:

```text
Check keys and the unit of analysis
   ↓
Join area data without multiplying rows
   ↓
Profile missing follow-up by deprivation
   ↓
Derive access groups and age bands
   ↓
Build follow-up time with censoring
   ↓
Deduplicate episodes into admissions
   ↓
Compute rates per 1,000 person-years
   ↓
Check baseline balance between groups
   ↓
Estimate adjusted and standardised effects
   ↓
Apply small-number suppression
   ↓
Capstone: incident respiratory admissions by deprivation
```

Each lab has two worked examples in R and Python, an editable runner, a quick check, and a prompt to change the data and predict the result.

## Synthetic Data

All records are invented and generated with a fixed seed. Field names are illustrative and do not follow the official IMD, HES or DfT schemas.

| Table | Rows | Contents |
| --- | --- | --- |
| `people` | 600 | Age, sex, disability, car access, programme participation, wellbeing at baseline and follow-up, missed appointments, exit date, fixed train/test split |
| `areas` | 40 | IMD decile, rurality, travel time to GP, bus frequency, car ownership, age structure, connectivity score |
| `admissions` | 931 | Emergency admission episodes 2019 to 2024 with diagnosis codes, including same-day duplicates and records after exit |
| `feedback` | 240 | Free-text comments from programme participants, coded by theme |
| `credhist` | 500 | `CredHist.csv` from the original course |

The data include deliberate problems (missing ages, missing follow-up, duplicate episodes, events after exit) so that the cleaning and validation steps have something real to catch. A browser runtime is not an approved environment for real patient or participant data.

## Running Locally

1. Open the course and go to **Data and downloads**.
2. Download the five CSVs and the companion script for your language.
3. Put them in one folder and run the script.

R needs `dplyr`, `tidyr`, `stringr` and `ggplot2`. Python needs `pandas`, `numpy`, `matplotlib`, `scikit-learn` and `statsmodels`.

## Known Limitations

- The original Sessions 3 and 11 shipped with slides only; their code in this edition is reconstructed from the slides.
- Session 10's API examples use postcodes.io in place of the original Guardian API and are not run in the browser.
- Parallel back-ends are not available in the browser runtimes, so the Session 11 lab compares loop and vectorised code; the parallel examples are shown for local use.
- Synthetic admission rates are deliberately high so a small cohort has enough events for the examples; they are not realistic estimates.
- Not every exercise has automated grading.

## Credits and Licence

This edition adapts:

> Gil-Clavel, S. (2025). *R-Course: R for Social Scientists* (Version 1.0) [Data set]. https://github.com/SofiaG1l/R_Course/. https://doi.org/10.5281/zenodo.17184812

The original course is released under the MIT licence. The Python translations, labs, practicum, capstone, synthetic data and interactive layer were added by Meron Kifle. If you use this material, please cite the original course.

## ☕ Support

If you find this course helpful, consider buying me a coffee!

<a href="https://buymeacoffee.com/qhl34mcne4">
  <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me a Coffee" height="60" width="217">
</a>
