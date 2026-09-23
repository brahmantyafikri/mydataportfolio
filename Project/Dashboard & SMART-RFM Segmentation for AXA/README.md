# AXA Policy Book Analytics & SMART-RFM Segmentation

A five-page Power BI policy book and an RFM/K-Means segmentation over 150,000
insurance policies — plus the data-quality page that shows the risk profile in
this book carries no measurable signal.

**Consulting-style project, Sains Data Consulting · 2025 · Power BI, scikit-learn, K-Means, RFM, Streamlit, PMBOK**

## Context

Insurance segmentation is still often done on agent intuition and broad
demographics. The brief was to replace that with clustering on actual customer
behaviour, and to deliver it the way a consultancy would — scope, RACI, budget,
timeline and a named strategy per segment, not a notebook.

## Data

150,000 customer records with policy dates, premium, coverage, claim history,
credit score, demographics, service contacts and a risk profile field.

## Part 1 — Policy Book Analytics dashboard

Five pages in Power BI, filterable by product, billing frequency, area type and
segmentation group:

| Page | Covers |
| --- | --- |
| Overview | 150K customers, $273.03M premium, $40bn coverage, 25.9% claim filing |
| Customer Profile | Age band, gender, occupation, education, income, preferred channel |
| Policy & Exposure | Renewal windows (37.5K inside 90 days), tenure bands, avg premium by product |
| Service & Engagement | Service contact bands, behavioural segment, claim history, driving record |
| Data Quality | Completeness, missingness by column, and signal tests |

## Part 2 — SMART-RFM segmentation

RFM built two ways, each scored with the Elbow method then K-Means:

| Combination | R | F | M | k | Silhouette | DBI |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Days since last renewal | Policy tenure | Premium | 4 | 0.2752 | 1.1698 |
| 2 | Days since last renewal | Claim count | Premium | 3 | 0.2643 | 1.3504 |
| Demographic | — | — | — | 3 | 0.1160 | 2.3950 |

Combination 1 segments, with the strategy attached to each:

| Cluster | Name | Profile | Strategy |
| --- | --- | --- | --- |
| 0 | Loyal High Value | Recent renewal, long tenure, high premium | Retention, loyalty rewards, upsell |
| 1 | New Comers | Recent renewal, short tenure, mid premium | Onboarding, product education |
| 2 | At-Risk Loyal | Lapsed renewal, long tenure, mid-high premium | Reactivation, renewal reminders, discount |
| 3 | Low Value | Lapsed renewal, short tenure, low premium | Selective promotion, needs survey |

**These silhouette scores are weak and the report says so.** 0.275 sits in the
"weak cluster" band — the segments are usable for targeting but they overlap,
and the recommendation is to monitor them rather than treat the boundaries as
real. The demographic-only model at 0.116 was reported as not usable.

## The finding worth leading with

The data-quality page tests whether the risk profile field means anything:

| Test | Result | Reading |
| --- | --- | --- |
| Highest Cramér's V, all feature-target pairs | 0.0061 | Below 0.1 is negligible |
| η² of numeric features vs Risk Profile | 0.00004 | Explains 0.004% of variance |
| Mean credit score by risk tier | 689 / 689 / 689 | High, Medium and Low are identical |
| High-risk share, clean vs major violations | 8.8% / 8.2% | Driving record carries no signal |
| Correlation, premium vs coverage | 0.0026 | Should be strongly positive if real |

The risk profile in this book does not separate anything. Worth knowing before
anyone prices against it.

## Files

| File | What it is |
| --- | --- |
| `Laporan Project SDC_Kelompok 12_SDA1.pdf` | Full report — method, results, strategy, contract, pricing |
| `PPT_FP_Kelompok12_SDC-A1.pdf` | Final presentation deck |
| `Screenshot ... 225827.png` | Dashboard: Overview |
| `Screenshot ... 225849.png` | Dashboard: Customer Profile |
| `Screenshot ... 225900.png` | Dashboard: Policy & Exposure |
| `Screenshot ... 225917.png` | Dashboard: Service & Engagement |
| `Screenshot ... 225930.png` | Dashboard: Data Quality |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p7
