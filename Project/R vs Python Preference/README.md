# R vs Python Preference Among Data Science Students

A Likert survey tested properly — and the headline result is that the
preference gap people assume exists does not show up.

**Survey study, Universitas Airlangga · 2023 · R, SPSS, Shiny, chi-square, Spearman, Mann-Whitney**

> *Analisis Preferensi Bahasa Pemrograman R dan Python dalam Penggunaan
> Praktikum, Tugas, dan Proyek Pribadi Mahasiswa Teknologi Sains Data 2022*

## Context

R and Python are both taught in the Data Science Technology programme, and
students hold strong opinions about which is better. The study asks whether
those opinions correspond to a measurable difference in comfort, difficulty,
mastery, frequency of use or visualisation preference — or whether it is just
tribal.

## Data

Primary data from a Google Form questionnaire distributed to Data Science
Technology students, 2022 cohort.

Preprocessing: missing values found in 8 variables; outliers identified as
points beyond the boxplot whiskers. Likert items were put through **validity
and reliability testing before any analysis** — all items passed.

## Method

| Data type | Test |
| --- | --- |
| Categorical | Chi-square test of association |
| Numeric | Spearman correlation |
| Main comparison | **Mann-Whitney U** |

## Results

### The main finding is a null result

**Mann-Whitney U: p = 0.9178 > α = 0.05.**

No significant difference between R and Python across comfort, difficulty,
mastery, frequency of use, or visualisation preference. The two languages are
statistically indistinguishable in how this cohort experiences them — the
preference is real as an opinion, but it does not correspond to a measurable
difference in use.

A null result reported as a null result, rather than sliced until something
turned significant.

### What did show up

| Finding | Detail |
| --- | --- |
| Programming is seen as essential | **85.3%** rated it "very important", 14.7% "important" — nobody said otherwise |
| Python mastery edges ahead | More respondents report mastering Python than R |
| Python comfort edges ahead | More respondents report being comfortable in Python |
| Gender split on mastery | Men lean toward Python; the male/female proportion is otherwise fairly balanced |

## Deliverable

Results published as a Shiny app so the charts stay explorable — pie, line,
Likert, boxplot, scatter and stacked bar views of the same survey.

## Files

| File | What it is |
| --- | --- |
| `preferensi.png` | Research poster — background, method, all charts, conclusions |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p6
