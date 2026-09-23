# NSCLC Stage Classification on CT Images

Undergraduate thesis staging non-small-cell lung cancer from CT volumes,
benchmarking a CNN against two Vision Transformers with Grad-CAM
interpretability.

**Undergraduate thesis, Universitas Airlangga · 2026 · PyTorch, DenseNet121, ViT-B/16, ViT-B/32, Grad-CAM**

> *Klasifikasi Stadium Non-Small Cell Lung Cancer (NSCLC) pada Citra CT Berbasis
> Deep Learning dan Transformer dengan Interpretabilitas Grad-CAM*

## Context

Staging NSCLC from CT is a hard, imbalanced problem: Stage III dominates the
data while Stage II is rare. A model can score respectably on accuracy by
quietly refusing to predict the minority class, which is exactly the failure a
clinical tool cannot have. The thesis asks two questions — does a transformer
beat a CNN here, and does either one look at the right part of the scan.

## Method

Six configurations: three architectures (DenseNet121, ViT-B/16, ViT-B/32) at two
slice depths (5 and 31 slices per patient). Augmentation applied per slice —
random rotation, affine shear/zoom/translate, horizontal and vertical flip.
Training ran to 45+ epochs with early stopping on validation loss (best epoch 26).

## Results

| Architecture | Slices | Accuracy | Macro Precision | Macro Recall | **Macro F1** |
| --- | --- | --- | --- | --- | --- |
| DenseNet121 | 5 | **0.726** | 0.437 | 0.437 | 0.426 |
| DenseNet121 | 31 | 0.661 | 0.377 | 0.373 | 0.359 |
| ViT-B/16 | 5 | 0.677 | 0.356 | 0.381 | 0.361 |
| ViT-B/16 | 31 | 0.661 | 0.394 | 0.388 | 0.384 |
| **ViT-B/32** | **5** | 0.710 | 0.430 | 0.444 | **0.432** |
| ViT-B/32 | 31 | 0.629 | 0.326 | 0.357 | 0.338 |

**Accuracy and macro F1 pick different winners.** DenseNet121 leads on accuracy
(0.726); ViT-B/32 leads on macro F1 (0.432). On data this imbalanced, macro F1
is the honest number, so ViT-B/32 at 5 slices is the selected model.

The confusion matrix explains the gap — **Stage II is never predicted at all**:

|  | Pred Stage I | Pred Stage II | Pred Stage III |
| --- | --- | --- | --- |
| **Actual Stage I** | 6 | 0 | 8 |
| **Actual Stage II** | 1 | 0 | 5 |
| **Actual Stage III** | 4 | 0 | 38 |

Second finding: **more slices made every architecture worse**, not better. All
six configurations drop when going from 5 to 31 slices.

## Interpretability

Grad-CAM was run over the model attributions to check where the decision
actually comes from. Activation sits on lung tissue rather than on the scanner
table, the body outline or other incidental artefacts — which is the minimum
bar before an imaging model is worth discussing clinically.

## Files

| File | What it is |
| --- | --- |
| `Screenshot ... 195424.png` | Thesis cover page |
| `Screenshot ... 195440.png` | Grad-CAM activations, ViT-B/16 at 31 slices |
| `Screenshot ... 195458.png` | Table 4.14 — all six configurations compared |
| `Screenshot ... 195450.png` | Confusion matrix, ViT-B/32 at 5 slices |
| `Screenshot ... 195516.png` | Training and validation loss, best epoch 26 |
| `Screenshot ... 195527.png` | The augmentation set applied to each slice |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p11
