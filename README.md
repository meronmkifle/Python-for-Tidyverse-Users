# Python for Tidyverse Users

A practical, side-by-side guide for translating R and tidyverse fluency into Python and pandas, from your first Python session through data cleaning, automated ETL pipelines, statistical analysis, machine learning, and production workflows.

<img width="569" height="194" alt="Python for Tidyverse Users" src="https://github.com/user-attachments/assets/771130b4-facf-4e97-9efc-5e59e230fc5a" />

## Who This Is For

This guide is designed for data analysts, researchers, data scientists, and other R users who already work comfortably with the tidyverse and want to become productive in Python without relearning data analysis from the beginning.

If you already know `dplyr`, `tidyr`, `ggplot2`, `stringr`, `lubridate`, or `purrr`, many of the underlying concepts will already be familiar.

The focus is therefore not just on teaching Python syntax. The guide shows how familiar R workflows translate into Python, where the two ecosystems behave differently, which differences can cause real bugs, and how to move from exploratory analysis toward reliable and automated data workflows.

## What Makes This Guide Different

Rather than presenting Python as an entirely new way of thinking, the guide uses R and the tidyverse as the reference point.

Where useful, concepts are presented side by side:

```text
R / tidyverse                Python / pandas

filter()                     query() / boolean masks
select()                     column selection
mutate()                     assign()
group_by()                   groupby()
summarise()                  agg()
pivot_longer()               melt()
pivot_wider()                pivot_table()
left_join()                  merge()
stringr                      .str
lubridate                    .dt / pandas datetime
purrr                        comprehensions / apply / map
```

The guide also goes beyond syntax translation by covering data quality, preprocessing, automation, validation, testing, reproducibility, and production considerations.

## What's Covered

| Section                           | Topics                                                                                                                                                                                                                                   |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Foundations**                   | Python setup, environments, syntax differences, 0-based indexing, indentation, method chaining, data types, lists, dictionaries, tuples, NumPy arrays, Series, and DataFrames                                                            |
| **Data Wrangling**                | `dplyr` to pandas mappings for selecting, filtering, mutating, summarising, grouping, joins, reshaping, strings, dates, categoricals, and window operations                                                                              |
| **Data Preprocessing & Cleaning** | Data profiling, schema checks, column standardisation, text cleaning, numeric conversion, currency parsing, date parsing, missing values, duplicate detection, category harmonisation, validation, invalid records, and outlier flagging |
| **Automated Data Cleaning**       | Reusable cleaning functions, cleaning reports, rejected-record quarantine, configuration-driven rules, batch processing, idempotence, logging, testing, and scheduled cleaning jobs                                                      |
| **ETL & Pipelines**               | Extract, transform, validate, and load patterns, data-quality checks, reproducible transformations, auditability, logging, failure handling, and end-to-end pipeline design                                                              |
| **APIs & Web Scraping**           | REST APIs, authentication, pagination, HTTP errors, timeouts, retries, rate limits, JSON processing, BeautifulSoup, and HTML table extraction                                                                                            |
| **SQL from Python**               | Database connections, SQLAlchemy, pandas SQL workflows, parameterised queries, database-side aggregation, and deciding what belongs in SQL versus pandas                                                                                 |
| **Visualisation**                 | `ggplot2` concepts translated to matplotlib and seaborn, chart design, annotations, analytical storytelling, and Plotly interactive visualisations                                                                                       |
| **Statistics**                    | Hypothesis tests, assumptions, effect sizes, confidence intervals, statistical significance, practical significance, and regression with statsmodels                                                                                     |
| **Machine Learning**              | scikit-learn preprocessing, train/test splits, pipelines, cross-validation, leakage prevention, model evaluation, baselines, and reproducible modelling                                                                                  |
| **Production Python**             | Functions, modules, type hints, docstrings, error handling, CLI scripts, project structure, virtual environments, dependency management, testing, and reproducibility                                                                    |
| **Cheat Sheet**                   | A quick R to Python reference for common tidyverse and pandas operations                                                                                                                                                                 |

## Data Cleaning and Preprocessing

A major focus of the guide is moving from one-off cleaning commands to systematic and reproducible data preparation.

The cleaning workflow follows a practical pattern:

```text
Raw data
   ↓
Profile the data
   ↓
Standardise schema and column names
   ↓
Clean text and categories
   ↓
Parse dates and numeric values
   ↓
Handle missing data
   ↓
Detect duplicates
   ↓
Validate business rules
   ↓
Flag or quarantine invalid records
   ↓
Enrich and transform
   ↓
Validate again
   ↓
Write trusted output
   ↓
Produce an audit / cleaning report
```

Examples include deliberately messy data so that cleaning techniques are demonstrated in context rather than only through isolated functions.

Topics include:

* Profiling missingness, cardinality, types, and distributions
* Defining the grain of a dataset
* Identifying business keys
* Standardising inconsistent column names
* Cleaning whitespace and text casing
* Parsing dirty currency and numeric fields
* Handling mixed and invalid date formats
* Treating missing values according to their business meaning
* Detecting exact and key-based duplicates
* Distinguishing invalid values from genuine outliers
* Harmonising inconsistent categorical values
* Validating pattern-based fields such as email addresses
* Preserving rejected records for investigation
* Producing cleaning metrics and audit information

## Automating Data Cleaning

The guide also demonstrates how exploratory cleaning code can be converted into reusable automation.

Instead of repeatedly running notebook cells manually, cleaning logic can be packaged into functions such as:

```python
clean, report = clean_orders(raw)
```

The resulting workflow can track:

```text
Input rows
Output rows
Rejected rows
Invalid dates
Invalid numeric values
Duplicates removed
Validation failures
```

The automation sections cover reusable cleaning functions, configuration-driven rules, processing multiple files, structured logging, rejected-record handling, idempotent transformations, automated tests, and scheduled execution.

The goal is to move from:

```text
"I cleaned this dataset"
```

to:

```text
"I have a reproducible process that cleans this dataset,
checks its assumptions, records what changed, and fails
clearly when the data no longer satisfies its contract."
```

## Running Examples

Where possible, the guide uses running examples rather than disconnected snippets.

For example, a deliberately messy customer-orders dataset is progressively:

1. Profiled
2. Standardised
3. Parsed
4. Cleaned
5. Validated
6. Deduplicated
7. Split into accepted and rejected records
8. Processed through reusable functions
9. Tested
10. Written to a trusted output format

This makes it easier to understand how individual pandas operations fit together into a realistic workflow.

## R to Python Mental Model

The central idea is that your analytical thinking already transfers.

You already understand concepts such as:

* Tidy data
* Filtering
* Grouping
* Aggregation
* Joins
* Reshaping
* Vectorised operations
* Missing data
* Statistical modelling
* Reproducible analysis

Python introduces different syntax and some important semantic differences, but the analytical foundations remain useful.

Particular attention is given to differences that can produce incorrect results, including:

* 0-based indexing
* Start-inclusive and end-exclusive slicing
* Scalar versus vectorised boolean operators
* Series versus DataFrame behaviour
* Index alignment
* `.loc` versus `.iloc`
* Missing-value semantics
* Join cardinality
* `groupby().agg()` versus `groupby().transform()`
* Datetime parsing
* Row-wise operations versus vectorisation
* Train/test leakage in machine learning

## From Analysis to Production

The later sections progressively move beyond interactive analysis toward production-oriented Python.

The guide introduces patterns such as:

```python
def extract(...):
    ...

def transform(...):
    ...

def validate(...):
    ...

def load(...):
    ...

def main():
    ...
```

It then builds on these with logging, validation rules, reusable modules, testing, environment management, automated cleaning, batch processing, and scheduling.

The aim is not simply to reproduce an R script in Python. It is to show how Python can extend an analyst's existing skills into data engineering, automation, machine learning, APIs, and production workflows.

## Quick Reference

The guide concludes with a comprehensive R to Python cheat sheet covering common operations across:

* `dplyr`
* `tidyr`
* `stringr`
* `lubridate`
* `purrr`
* `ggplot2`
* pandas
* NumPy
* matplotlib
* seaborn
* scipy
* statsmodels
* scikit-learn

Use the cheat sheet for syntax lookup, and the main chapters for the conceptual differences, failure modes, examples, and production patterns behind that syntax.

## Suggested Learning Path

If you already use the tidyverse regularly, a practical path through the guide is:

```text
Python foundations
        ↓
pandas fundamentals
        ↓
select / filter / mutate / groupby
        ↓
joins and reshaping
        ↓
strings and dates
        ↓
data preprocessing and cleaning
        ↓
automated cleaning
        ↓
ETL pipelines
        ↓
SQL and APIs
        ↓
visualisation and statistics
        ↓
machine learning
        ↓
production Python
```

You do not need to abandon R to become productive in Python.

The goal is to make the two ecosystems complementary: use the analytical intuition you already developed with the tidyverse, while adding Python's broader ecosystem for automation, engineering, machine learning, APIs, and production data workflows.
