# HDI, Unemployment & Poverty Across Indonesian Provinces

Provincial welfare modelled with spatial regression, because Moran's I proved
the provinces are not independent observations.

**Official Statistics research project, Universitas Airlangga · 2024 · Python, R, SVR, Spatial Error/Lag, K-Means++, GeoPandas**

> *Analisis Komprehensif Dinamika IPM, Pengangguran, dan Kemiskinan Indonesia
> Tahun 2022–2024*

## Context

The standard approach to provincial welfare data is OLS on HDI (IPM), open
unemployment (TPT) and poverty. That assumes each province is an independent
draw, which is false — poverty in one province is entangled with its
neighbours. The study tests that assumption first and then picks the model.

## Data

BPS (Statistics Indonesia) provincial figures for 2022–2024: Human Development
Index, Open Unemployment Rate, and poverty rate.

## Method

1. **Correlation** — Spearman, because the distributions are skewed
2. **Spatial autocorrelation** — Moran's I to test province independence
3. **Regression** — SVR (RBF kernel, 100 estimators) under several target transformations, plus Spatial Error and Spatial Lag models
4. **Clustering** — K-Means++ with Elbow for k, to group provinces by welfare profile
5. **Thematic mapping** — poverty by province

## Results

### Correlation is weaker than expected

| Pair | Spearman ρ |
| --- | --- |
| HDI ↔ Poverty | −0.535 |
| Unemployment ↔ HDI | +0.393 |
| Unemployment ↔ Poverty | −0.312 |

Unemployment correlates *negatively* with poverty, which runs against the
usual intuition and is flagged in the report as not matching general theory.

### Space matters

Moran's I: **p = 0.001**. Significant spatial autocorrelation, so spatial
regression is required rather than optional.

### Model comparison

| Model | R² | RMSE | MAE | MAPE |
| --- | --- | --- | --- | --- |
| Yeo-Johnson + SVR | **0.59** | 3.04 | 2.25 | 24.38% |
| Square-root + SVR | 0.55 | 0.47 | 0.37 | 12.50% |
| Spatial Error Model (SEM) | 0.26 | 4.18 | 3.15 | 38.06% |
| Spatial Lag Model (SLM) | 0.24 | 4.23 | 3.14 | 37.05% |

SEM beats SLM among the spatial specifications. Under SEM:

| Predictor | p-value | Significant? |
| --- | --- | --- |
| Mean HDI | 0.027 | Yes |
| Mean unemployment | 0.198 | **No** |

**Only HDI significantly predicts poverty.** Open unemployment does not — human
development moves the needle, joblessness on its own does not.

### Five province clusters

K-Means++ produced five welfare profiles, silhouette 0.389. Each cluster got
its own policy recommendation, since a single national programme does not fit a
map where Papua and NTT sit at one extreme and Java, Sumatra and Kalimantan at
the other.

## Files

| File | What it is |
| --- | --- |
| `UAS_OS-A2_Kelompok 1.pdf` | Full paper in journal format |
| `UAS_OS-A2_Kelompok 1_PPT.pdf` | Presentation deck |
| `Screenshot ... 195237.png` | Thematic map — poverty concentrated in the east |
| `Screenshot ... 195219.png` | Spearman correlation matrix |
| `Screenshot ... 195229.png` | Cluster scatterplot matrix |
| `Screenshot ... 195247.png` | Policy recommendation per cluster |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p2
