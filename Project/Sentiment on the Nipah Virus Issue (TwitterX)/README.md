# Nipah Virus Sentiment on X/Twitter

Two sentiment methods on the same 207 posts disagree about half the negatives
— which is itself the finding.

**Social listening study · 2026 · Python, lexicon scoring, transformer sentiment, WordCloud**

## Context

Public-health monitoring usually runs one sentiment method and reports the
number. This ran two on identical data to see how much the choice of method
decides the answer.

## Data

207 Indonesian X/Twitter posts about the Nipah virus outbreak, collected across
January 2026 (3 Jan – 2 Feb).

## Results

### The two methods do not agree

| Sentiment | Lexicon | Transformer | Difference |
| --- | --- | --- | --- |
| Negative | 39 | **85** | +46 |
| Neutral | 140 | 107 | −33 |
| Positive | 28 | 15 | −13 |

The lexicon reads 19% of posts as negative. The transformer reads 41%. Roughly
a quarter of the corpus moves between categories depending on which tool you
pick.

For a public-health dashboard that is the difference between reporting *"the
public is calm, mostly informational"* and *"two in five posts are alarmed"* —
and those two reports lead to different decisions.

### Where they agree: the timeline

Both methods produce the same shape.

| Period | Activity |
| --- | --- |
| 3–24 Jan | Near silence, 0–6 posts/day |
| 25–26 Jan | Sharp rise |
| **27 Jan** | **Peak — 16 negative posts in one day** |
| 28 Jan – 2 Feb | Elevated but declining |

The event detection is robust. The magnitude is not.

### What the conversation was actually about

Dominant terms: **hewan** (animal), **penularan** (transmission),
**kesehatan** (health), **penyakit** (disease), **kelelawar** (bat),
**kewaspadaan** (vigilance), **gejala** (symptoms), **wabah** (outbreak),
**babi** (pig), **karantina** (quarantine), **malaysia**, **thailand**, **who**.

This is a reporting vocabulary, not a panic vocabulary — transmission routes,
symptoms, precautions and which countries are affected. Which supports the
lexicon's more conservative reading, and is a useful argument against taking
the transformer's 41% at face value.

## Takeaway

Report the method alongside the number, or report both. A single sentiment
percentage with no stated method is not a finding.

## Files

| File | What it is |
| --- | --- |
| `Screenshot ... 200848.png` | Word cloud — what the conversation was about |
| `Screenshot ... 200838.png` | Transformer vs lexicon, side by side |
| `Screenshot ... 200820.png` | Lexicon distribution |
| `Screenshot ... 200823.png` | Daily trend, lexicon |
| `Screenshot ... 200833.png` | Daily trend, transformer |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p14
