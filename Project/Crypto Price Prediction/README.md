# BitCast — Bitcoin Price Prediction

A multi-output LSTM forecasting Bitcoin 12 steps ahead, shipped as a public web
app with its own methodology page.

**Machine Learning project, Universitas Airlangga · 2025 · TensorFlow/Keras, LSTM, technical indicators**

> *Sistem Informasi Prediksi Harga dan Pergerakan Pola Cryptocurrency Bitcoin*

**Live:** [bitcast.fly.dev](https://bitcast.fly.dev)

## Context

Indonesia has over 12 million crypto investors and financial literacy has not
kept pace, which produces impulsive, high-risk decisions. BitCast was built to
be accurate *and* legible to a non-expert — a prediction system that shows its
working rather than emitting a number.

## Data

| | |
| --- | --- |
| Asset | Bitcoin (BTC/USDT) |
| Interval | 4 hours |
| Training period | 2 Nov 2017 – 2 Dec 2023 |
| Test period | 2 Dec 2023 – 8 Jun 2025 |
| Input shape | 258 timesteps (≈43 days) × 9 features |
| Features | 9 selected indicators — Close, RSI, OBV and others |

## Model

```
Input (258 × 9)
   │
LSTM(528) ──> Dropout(0.4)
   │
LSTM(256) ──> Dropout(0.4)
   │
Dense(12)  ──> t+1 … t+12
```

| Setting | Value |
| --- | --- |
| Optimizer | Adam, lr = 1e-3 |
| Loss | MSE |
| Regularisation | EarlyStopping + ReduceLROnPlateau |
| Cross-validation | 10-fold TimeSeriesSplit |
| Batch size | 128 |
| Epochs | max 300 |

A single network emits all twelve horizons at once rather than being called
recursively, which stops prediction error compounding step over step.

## Results

| Horizon | MAE | RMSE | MSE |
| --- | --- | --- | --- |
| t+1 | 0.04318 | 0.06263 | 0.00392 |
| t+12 | 0.06024 | 0.08025 | 0.00644 |

Error grows about 40% across twelve steps — as expected, and gently enough that
the far horizon is still informative. On scaled values.

Cross-validation is 10-fold `TimeSeriesSplit`, so no future data leaks backwards
into training — the standard trap in price forecasting.

## The product

| Page | What it does |
| --- | --- |
| Exchange | Live BTC price, interactive chart from 15m to 1d, 24h volume and market cap |
| Predict | LSTM projection over the coming horizons |
| Model & Methodology | Data collection, feature engineering, architecture, training and validation — written out in full |

The methodology page is deliberate: a prediction UI that does not explain itself
is indistinguishable from a guess, and this audience is exactly the one that
cannot tell the difference.

## Files

| File | What it is |
| --- | --- |
| `bitcoin.png` | Project poster — architecture, data, metrics, product screens |

## On the portfolio

https://mydataportfolio-six.vercel.app/#p8
