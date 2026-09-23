# Nutri-Score Classification of Beverages

449 packaged drinks graded A to E from their nutrition labels — once the labels
were parsed back into numbers.

**Data Mining I project, Universitas Airlangga · 2024 · Python, scikit-learn, Random Forest, Decision Tree**

> *Klasifikasi Nutrition-Score pada Minuman Berdasarkan Kandungan Gizi*

## Context

Nutri-Score is the European front-of-pack A–E grade. The question was whether
the grade can be recovered from the raw nutrition panel alone, and which
nutrients actually drive it.

## Data

449 beverages, 9 per-100ml features → 1 target (Nutri-Score A–E).

| Feature | |
| --- | --- |
| Energy | Carbohydrates | 
| Fat | Sugars |
| Saturated fat | Fiber |
| Proteins | Salt |
| Fruits, vegetables and legumes (%) | |

Class balance: C is the most common grade, then E, B, D, with A rarest.

## The unglamorous part

Most of the work was parsing, not modelling. The raw columns were free text:

| Stored as | Needs to be |
| --- | --- |
| `1,577 kj (373 kcal)` | `373` |
| `2.8 g` | `2.8` |
| `< 0.5 g` | `0.5` |
| `?` | missing |
| `Nutri-Score D` | `D` |

A symbol audit ran over every column to find what was actually in there before
any cleaning rule was written. After parsing: label encoding, outlier handling,
scaling, then a 70/30 split.

## Results

| Model | Accuracy | Macro Precision | Macro Recall | Macro F1 |
| --- | --- | --- | --- | --- |
| **Random Forest** | **96.30%** | 0.9594 | 0.9616 | **0.9600** |
| Decision Tree | 95.56% | 0.9523 | 0.9595 | 0.9550 |

Both are strong and close. The single tree is only 0.74 points behind, which
matters if someone has to justify a grade to a regulator or a consumer — a
readable tree is easier to defend than an ensemble.

### They disagree about *why*

| Feature | Random Forest | Decision Tree |
| --- | --- | --- |
| Fat | 0.242 | **0.770** |
| Energy | 0.235 | ~0 |
| Proteins | 0.214 | ~0 |
| Saturated fat | 0.189 | 0.199 |
| Fiber | 0.111 | 0.024 |
| Sugars | ~0 | ~0 |

Random Forest spreads importance across four nutrients; the Decision Tree puts
77% of its weight on fat alone and ignores the rest. Same accuracy, very
different explanation — a reminder that feature importance describes the model,
not the world.

**Sugar contributes almost nothing in either model**, which looks wrong until
you notice sugar correlates 0.79 with energy. It is already in the model, just
wearing a different name.

## Files

| File | What it is |
| --- | --- |
| `DM1_SD_A1_*.ipynb` | Full notebook — parsing, EDA, both models |
| `DM1_SD-A1_*.pdf` | Written report |
| `Screenshot ... 200536.png` | Pearson correlation heatmap + class balance |
| `Screenshot ... 200600.png` | Random Forest confusion matrix |
| `Screenshot ... 200544.png` | Random Forest feature importance |
| `Screenshot ... 200556.png` | Decision Tree confusion matrix |
| `Screenshot ... 200550.png` | Decision Tree feature importance |
| `Screenshot ... 200526.png` | Boxplots — every field is right-skewed |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p13
