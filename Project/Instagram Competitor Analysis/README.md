# Instagram Competitor Analysis

Six Indonesian research and data firms scraped, classified and read as one
competitive set — then handed over as a live Power BI monitor.

**Market analysis for BeData Technology Indonesia · 2025 · Python, Apify, rule-based NLP, Power BI**

## Context

BeData needed to know where it sat against the other Indonesian research and
data firms on Instagram: who is selling hardest, who is recruiting respondents,
who is talking to business and who is talking to everyone — and where the gap
is that nobody is covering.

## Data

| Brand | Posts classified | Comments |
| --- | --- | --- |
| compas.co.id | 424 | 849 |
| bedata.id | 224 | 234 |
| populix.co | 200 | 162 |
| frontiercoid | 79 | 32 |
| infovesta.id | 79 | 57 |
| poltracking | 70 | 358 |
| **Total** | **1,076** | **1,692** |

Plus website copy for five of the six, scraped separately.

## Method

Captions classified on three axes with a rule-based pass: **call-to-action**
(sales-led / product-led / engagement / none), **target market** (business,
government, academic, public, general) and **message type** (business offering,
respondent acquisition, brand legitimacy, methodology trust, event activation,
political domain, other).

## Results

### Call-to-action mix (% of captions)

| Brand | Sales-led | Product-led | Engagement | None |
| --- | --- | --- | --- | --- |
| compas.co.id | **46.2** | 20.3 | 5.0 | 28.5 |
| populix.co | 16.0 | 26.5 | 5.0 | 52.5 |
| bedata.id | 12.1 | 11.2 | 12.1 | 64.7 |
| frontiercoid | 10.1 | 11.4 | 10.1 | 68.4 |
| infovesta.id | 7.6 | 2.5 | 1.3 | 88.6 |
| poltracking | 2.9 | 0.0 | 0.0 | **97.1** |

### Target market (% of captions)

| Brand | Business | General | Government | Academic | Public |
| --- | --- | --- | --- | --- | --- |
| compas.co.id | **97.6** | 0.9 | 0.7 | 0.7 | 0.0 |
| frontiercoid | 60.8 | 22.8 | 12.7 | 1.3 | 2.5 |
| populix.co | 53.0 | 17.0 | 17.5 | 2.0 | 10.5 |
| bedata.id | 24.1 | 49.1 | 9.8 | 14.3 | 2.7 |
| infovesta.id | 10.1 | **84.8** | 3.8 | 1.3 | 0.0 |
| poltracking | 1.4 | 31.4 | **67.1** | 0.0 | 0.0 |

### Reading

- **Compas is the commercial outlier** — nearly half its captions carry a
  sales-led CTA and almost everything is aimed at a business audience.
- **Poltracking barely sells at all** — 97.1% of captions carry no CTA, and
  two-thirds address government and politics.
- **Populix leads on respondent acquisition** at 27.8% of captions.
- **The open gap:** a general, non-corporate audience approached with a
  product-led message. Nobody in the set was working it.

## Deliverable

A four-page Power BI monitoring dashboard rather than a static report, so the
client could keep watching the set afterwards:

| Page | Covers |
| --- | --- |
| Overview | 668 posts in window, 79K likes, 2K comments, 121.11 avg engagement |
| Performa Konten | Likes/posts/engagement by brand, post type and weekday |
| Analisis Komentar | Per-brand comment browser, length distribution, word cloud |
| Detail Brand | Timeline, post-type preference, best day to post |

Monday is the strongest day at 242.32 average engagement; Tuesday the weakest
at 86.93.

## Files

```
Code/          notebooks for caption, comment and content analysis
Data Bersih/   cleaned per-brand posts and the three distribution tables
Raw Data/      Apify scrape output, per-brand comments, post URLs, website copy
Support Dokumen/  project brief and client document
Screenshot ... 0954xx.png   the four dashboard pages
```

> **Note.** `Raw Data/` contains public Instagram data as scraped, including
> commenter usernames and comment text.

## On the portfolio

https://mydataportfolio-six.vercel.app/#p4
