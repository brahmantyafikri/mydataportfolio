# Project source material

The evidence behind every case study on
[mydataportfolio-six.vercel.app](https://mydataportfolio-six.vercel.app) —
reports, decks, notebooks, datasets and figures. Each folder has its own README
with the method and the actual numbers.

| # | Project | Field | Headline result |
| --- | --- | --- | --- |
| 01 | [Telkomsel Chatbot RAG](./Telkomsel%20Chatbot%20RAG) | GenAI · RAG | 19/19 black-box scenarios passed, 5 n8n workflows |
| 02 | [AXA Policy Book & SMART-RFM](./Dashboard%20%26%20SMART-RFM%20Segmentation%20for%20AXA) | Analytics · BI | 150,000 policies, 5 dashboard pages; risk profile carries no signal |
| 03 | [NSCLC Stage Classification](./Thesis%20NSCLC%20Stage%20Classification) | ML · Medical imaging | ViT-B/32 macro F1 0.432 — accuracy and F1 pick different winners |
| 04 | [HDI, Unemployment & Poverty](./HDI%2C%20Unemployment%20%26%20Poverty) | Econometrics · Spatial | SVR R² 0.59; Moran's I p = 0.001; unemployment not significant |
| 05 | [Instagram Competitor Analysis](./Instagram%20Competitor%20Analysis) | NLP · Competitive intel | 1,076 captions and 1,692 comments classified across 6 brands |
| 06 | [Vehicle Type Classification](./Vehicle%20Type%20Classification) | ML · Vision | 95% with ResNet50 vs 29% from scratch |
| 07 | [Health Question Summarization](./Health%20Question%20Summarization) | NLP · Transfer learning | ROUGE-1 lifted 0.298 → 0.499 by fine-tuning |
| 08 | [BitCast — Bitcoin Price Prediction](./Crypto%20Price%20Prediction) | ML · Time series | Stacked LSTM, MAE 0.043 at t+1 |
| 09 | [Nutri-Score Classification](./Nutri-Score%20Classification%20of%20Beverages%20Based%20on%20Nutritional%20Content) | ML · Classification | Random Forest 96.3%, macro F1 0.960 |
| 10 | [AI Agent Sentiment: Global vs Indonesia](./AI%20Agent%20Sentiment%20Global%20vs%20Indonesia) | NLP · Cross-lingual | EN 31% positive vs ID 73.8% neutral |
| 11 | [Nipah Virus Sentiment on X](./Sentiment%20on%20the%20Nipah%20Virus%20Issue%20%28TwitterX%29) | NLP · Public health | Lexicon 39 negatives, transformer 85 — on the same 207 posts |
| 12 | [Urban vs Rural Poverty](./Urban%20vs%20Rural%20Poverty%20Rates%20Across%20Indonesian%20Provinces%20%28March%202023%29) | Nonparametric stats | Rural 12.61% vs urban 7.11%, p = 1.4 × 10⁻⁷ |
| 13 | [Sugar Risk Content on TikTok](./TikTok%20Content%20Analysis%20on%20the%20Dangers%20of%20Sugar%20Consumption) | Content analysis | 50 videos coded; 66.7% educational, only 10% offer an alternative |
| 14 | [R vs Python Preference](./R%20vs%20Python%20Preference) | Survey · Statistics | Mann-Whitney p = 0.918 — no significant difference |

## By field

- **GenAI** — 01
- **Machine learning** — 03, 06, 08, 09
- **NLP** — 05, 07, 10, 11
- **Analytics, BI & statistics** — 02, 04, 12, 13, 14

## A note on the numbers

Every figure quoted on the portfolio site traces to something in this folder. A
few of these are null or weak results — the AXA silhouette scores are poor and
reported as poor, the R vs Python comparison found no difference, and the NSCLC
model never predicts Stage II. They are written up that way on purpose.

## A note on the data

Some folders contain group coursework naming other students, and
`Instagram Competitor Analysis/Raw Data/` contains public Instagram data as
scraped, including commenter usernames and comment text.
