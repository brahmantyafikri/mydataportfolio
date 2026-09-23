# Vehicle Type Classification

Cars, buses and trucks classified for automated toll-gate sorting. Three
architectures under identical conditions — and the gap between them is the
result.

**Data Mining II project, Universitas Airlangga · 2024 · TensorFlow, CNN, ResNet50, VGG19**

## Context

Indonesian toll gates classify vehicles by type to set the tariff, still largely
by eye. The question was whether a vision model could do it reliably enough on
ordinary photographs — and whether a purpose-built CNN or a pre-trained backbone
is the right tool at a realistic dataset size.

## Data

1,961 images scraped from Pinterest and Google across three classes — Mobil
Biasa (car), Bus, Truck — roughly balanced at ~650 each. 393 images held out
for testing.

## Results

| Model | Accuracy | Macro F1 |
| --- | --- | --- |
| **ResNet50** | **95%** | 0.95 |
| VGG19 | 93% | 0.93 |
| CNN from scratch | 29% | 0.17 |

**The gap is the finding.** A CNN built from scratch lands at 29% — barely
above the 33% you would get by guessing on three classes. The same data through
a pre-trained backbone reaches 95%. At this dataset size transfer learning is
not an optimisation, it is the difference between a working classifier and a
broken one.

### Confusion matrix, ResNet50

|  | Pred Car | Pred Bus | Pred Truck |
| --- | --- | --- | --- |
| **Actual Car** | 137 | 0 | 3 |
| **Actual Bus** | 1 | 98 | 6 |
| **Actual Truck** | 4 | 5 | 139 |

Every meaningful error is a bus/truck confusion — 6 buses read as trucks, 5
trucks as buses. A car is essentially never mistaken for either. For a toll
operator that is the survivable failure mode: the two classes that get confused
are the two large-vehicle categories, not the one that sets a very different
tariff.

### Real-world spot check

Three photographs outside the test set — a bus with motion blur, a car in bright
light, a decorated truck at night:

| Image | ResNet50 | VGG19 | CNN |
| --- | --- | --- | --- |
| Bus, slight noise | Bus ✓ | Bus ✓ | Bus ✓ |
| Car, bright light | Car ✓ | Car ✓ | Car ✓ |
| Truck, night | Truck ✓ | Truck ✓ | Bus ✗ |

## Files

| File | What it is |
| --- | --- |
| `DM2_A2_014_034_046_094.ipynb` | Full notebook — preprocessing, three models, evaluation |
| `DM2_A2_014_034_046_094.pdf` | Written report |
| `DM2_014_034_046_094_PPT.pdf` | Presentation deck |
| `Screenshot ... 222242.png` | Real-world predictions across all three models |
| `Screenshot ... 222112.png` | ResNet50 accuracy and loss over ten epochs |
| `Screenshot ... 222219.png` | Confusion matrix |
| `Screenshot ... 222325.png` | Class balance across the 1,961 images |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p3
