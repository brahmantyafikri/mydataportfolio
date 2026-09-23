# Urban vs Rural Poverty Across Indonesian Provinces

Rural poverty runs five and a half points above urban — held up by six
nonparametric tests rather than a glance at the bar chart.

**Applied statistics study, Universitas Airlangga · 2023 · Python, Wilcoxon, Kruskal-Wallis, Jonckheere-Terpstra, Kendall's tau**

> *Analisis Persentase Penduduk Miskin di Perkotaan dan Pedesaan Indonesia:
> Studi Kasus Provinsi pada Bulan Maret 2023*

## Context

"Rural poverty is worse than urban" is easy to assert and rarely tested
properly. This project treats it as a hypothesis and runs the tests the data
actually permits.

## Data

BPS provincial poverty rates, March 2023.

| | n | Mean | Std | Min | Median | Max |
| --- | --- | --- | --- | --- | --- | --- |
| **Urban (Perkotaan)** | 34 | 7.11% | 2.78 | 3.54% | 6.48% | 14.21% |
| **Rural (Pedesaan)** | 33 | 12.61% | 7.18 | 4.72% | 11.87% | 34.49% |

## Method — and why

Kolmogorov-Smirnov rejected normality for both distributions. That rules out
the parametric defaults and sends the whole analysis nonparametric.

| Question | Test | Result | Conclusion |
| --- | --- | --- | --- |
| Do the paired distributions differ? | Wilcoxon signed-rank | p = 0.00000014 | **Yes** — reject H₀ |
| Do the paired means differ? | Paired t-test | p = 0.000071 | **Yes** — reject H₀ |
| Are urban and rural related? | Kendall's tau | p = 0.0064 | **Yes**, but weakly |
| Do the six islands have identical distributions? | Kruskal-Wallis | p = 0.415 | **No difference** — fail to reject |
| Do the islands follow an ordered trend? | Jonckheere-Terpstra | p < 0.001 | **Yes** — ordered medians |

## Reading

1. **The gap is real.** Rural poverty is significantly higher, and at
   p = 1.4 × 10⁻⁷ it is not the work of a few outliers. Rural spread is also
   far wider (std 7.18 vs 2.78) — the worst rural province is at 34.49% while
   the worst urban province is at 14.21%.

2. **Correlated, but only weakly.** A province with low urban poverty is *not*
   reliably a province with low rural poverty. The two need separate policy —
   one poverty number per province hides the thing that matters.

3. **Kruskal-Wallis and Jonckheere-Terpstra disagree, and that is informative.**
   The six islands share a distribution *shape* (K-W fails to reject) but their
   medians do *rank* (J-T is significant). Testing only for difference would
   have concluded "no island effect" and missed a real ordering.

## Files

| File | What it is |
| --- | --- |
| `UAS_SNP_Kelompok J (10)_Poster.png` | Full study as presented — every test and result |
| `UAS_SNP_Kelompok J (10)_Laporan.pdf` | Written report |
| `Screenshot ... 201146.png` | Urban and rural poverty stacked by province |
| `Screenshot ... 201149.png` | Distribution histograms — neither is normal |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p16
