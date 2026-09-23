# Consumer Health Question Summarization

Six pre-trained summarizers benchmarked on Indonesian consumer health
questions, then the winner fine-tuned — ROUGE-1 from 0.298 to 0.499.

**Applied NLP research · 2025 · UnifiedQA-T5, mT5, mBART-50, Pegasus, T5-Large, ROUGE & BLEU**

> *Consumer Health Question Summarization Berbasis Transfer Learning untuk
> Bahasa Indonesia*

## Context

People asking health questions online write long, rambling posts with a lot of
background before the actual question. That makes a telemedicine triage queue
slow to read and makes search return the wrong answers. The task: compress each
post into a single answerable question without losing the clinical meaning.

## Data

Consumer health questions from Alodokter discussion threads. Preprocessing:
text cleaning, language normalisation, tokenisation, common-word filtering, and
stopword removal — the last of which was ablated rather than assumed.

## Method

```
Alodokter questions
      │
  preprocessing ──────────────┐
      │                       │
  six summarizers        with / without
      │                    stopwords
  ROUGE + BLEU evaluation ────┘
      │
  pick best model (UnifiedQA-T5)
      │
  fine-tune ──> re-evaluate
```

## Results

### Benchmark, before fine-tuning

| Model | ROUGE-1 | ROUGE-2 | ROUGE-L | BLEU |
| --- | --- | --- | --- | --- |
| **Unifiedqa-T5** | **0.2982** | **0.0810** | **0.2496** | **6.8375** |
| T5-Large | 0.2901 | 0.0761 | 0.2340 | 5.4499 |
| Msmarco-mT5 | 0.2564 | 0.0688 | 0.2092 | 4.2615 |
| Cendol-mT5 | 0.2397 | 0.0659 | 0.1941 | 3.4285 |
| mBART-large-50 | 0.2134 | 0.0673 | 0.1793 | 3.0429 |
| Pegasus | 0.0403 | 0.0073 | 0.0349 | 1.1245 |

UnifiedQA-T5 leads on every ROUGE metric. Pegasus collapses — ROUGE-1 0.0403,
effectively unusable on Indonesian.

Stopword removal helped some models and hurt others, which is why it was tested
both ways rather than applied by default.

### After fine-tuning UnifiedQA-T5

| Metric | Before | After | Change |
| --- | --- | --- | --- |
| ROUGE-1 | 0.2982 | **0.4992** | +67% relative |
| ROUGE-2 | 0.0810 | **0.2800** | +246% relative |
| ROUGE-L | 0.2496 | **0.4760** | +91% relative |

### Where it still fails

Scoring question by question shows the limit is the input, not the model:

| Question | ROUGE-1 |
| --- | --- |
| "Bagaimana cara menanganinya gimana?" | 0.000 |
| "Cara mengatasi masuk angin sembelit" | 0.308 |
| "Bagaimana cara mengatasi biduran setelah mandi?" | 0.333 |
| "Cara mengatasi siku tangan sebelah kanan" | 0.462 |
| "Bagaimana cara mengganjal sesak napas dan faringitis?" | 0.462 |

Vague questions score zero. The model cannot recover a specific question from a
post that never asked one.

## Files

| File | What it is |
| --- | --- |
| `Screenshot ... 195853.png` | Paper — abstract and introduction |
| `Screenshot ... 195901.png` | Research flowchart |
| `Screenshot ... 195910.png` | Table 1 benchmark + Table 2 fine-tuned result |
| `Screenshot ... 195916.png` | Full ablation, with and without stopwords |
| `Screenshot ... 195924.png` | Sample summaries scored individually |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p9
