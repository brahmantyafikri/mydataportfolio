# AI Agent Sentiment: Global vs Indonesia

Same product launch, two languages, two completely different receptions.

**Social listening study · 2026 · Python, X/Twitter scraping, cross-lingual sentiment, WordCloud**

## Context

When an open-source AI agent broke out in February 2026, the English and
Indonesian conversations about it looked nothing alike. This tracks both over
the same window, scoring each language separately so neither gets flattened by
translating it into the other.

## Data

| | English | Indonesian |
| --- | --- | --- |
| Posts | 100 | 84 |
| Window | ~19 days, February 2026 | same |

## Results

### Sentiment composition

| | Negative | Neutral | Positive |
| --- | --- | --- | --- |
| **English** | 16.0% | 53.0% | **31.0%** |
| **Indonesian** | 11.9% | **73.8%** | 14.3% |

English is polarised and opinionated — nearly a third positive, a sixth
negative. Indonesian is overwhelmingly neutral, with positive sentiment less
than half the English rate.

### Volume behaves differently too

| | Baseline | Peak |
| --- | --- | --- |
| **English** | ~0–2/day for 17 days | **93 posts in one day** |
| **Indonesian** | steady 1–9/day throughout | 22 posts |

English sat near silent and then detonated. Indonesian accumulated steadily
from day one and rose to a peak. **Global attention arrives as an event; local
attention accumulates.**

### They are talking about different things

| | Dominant vocabulary |
| --- | --- |
| **English** | user, AI, agent, open source, API, security, vulnerabilities, automation, assistant, build, control |
| **Indonesian** | user, AI, bisa, install, setup, pakai, gratis, coba, bikin, akses, whatsapp, telegram |

English is arguing about what the thing *means* — capability, risk, openness,
who controls it. Indonesian is working out how to *run* it — install, setup,
which platform, is it free.

## Reading

For anyone launching a developer tool into both markets, this is the actionable
part: English-language communication has to address risk and governance because
that is already the conversation. Indonesian-language communication has to
address setup and access, because that is where the attention actually is. The
same press release will underperform in one of the two.

## Files

| File | What it is |
| --- | --- |
| `Screenshot ... 200420.png` | English vs Indonesian, 100% stacked |
| `Screenshot ... 200335.png` | English sentiment distribution |
| `Screenshot ... 200356.png` | Indonesian sentiment distribution |
| `Screenshot ... 200341.png` | English volume trend — the 93-post spike |
| `Screenshot ... 200403.png` | Indonesian volume trend |
| `Screenshot ... 200345.png` | English word cloud |
| `Screenshot ... 200409.png` | Indonesian word cloud |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p12
