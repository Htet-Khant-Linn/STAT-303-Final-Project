# Benchmarking RNN, LSTM, and GRU for Multivariate Oil Price Forecasting

## Overview

This project benchmarks three deep learning architectures — Recurrent Neural Network (RNN), Long Short-Term Memory (LSTM), and Gated Recurrent Unit (GRU) — for multivariate crude oil price forecasting.

Using historical Brent and WTI crude oil prices along with financial and geopolitical indicators, the project evaluates how effectively each recurrent architecture predicts next-day oil prices.

The study was completed as the final project for **STAT 303** at **Parami University**.

---

# Project Objectives

The primary goals of this project are to:

* Forecast Brent and WTI crude oil prices
* Compare the predictive performance of:

  * Simple RNN
  * LSTM
  * GRU
* Analyze the effect of model complexity on financial time-series forecasting
* Investigate whether advanced recurrent architectures outperform simpler models

---

# Dataset

Dataset Source:

* Kaggle: *Global Oil Prices and Geopolitical Events Dataset*

The dataset contains daily records from **2010–2026** with approximately **4,000 trading-day observations**.

### Selected Features

#### Target Variables

* `brent_price`
* `wti_price`

#### Predictor Variables

* `dxy_index` — U.S. Dollar Index
* `vix` — Volatility Index
* `gpr_index` — Geopolitical Risk Index
* `event_severity` — Geopolitical event severity score

---

# Methodology

## Data Preprocessing

* Chronological 80/20 train-test split
* MinMax normalization
* Sequence window generation (20 trading days)
* Double-scaler strategy to avoid data leakage

## Model Architectures

All models use:

* Two recurrent layers
* Dropout regularization
* Dense output layer for multi-output prediction

### Compared Models

* Simple RNN
* LSTM
* GRU

## Training Configuration

* Optimizer: Adam
* Loss Function: Mean Squared Error (MSE)
* Epochs: 50
* Batch Size: 32
* Validation Split: 10%
* EarlyStopping applied

---

# Evaluation Metrics

The models were evaluated using:

* RMSE (Root Mean Squared Error)
* MAE (Mean Absolute Error)
* MAPE (Mean Absolute Percentage Error)

---

# Results

## Final Performance

| Model | Brent RMSE | Brent MAPE | WTI RMSE | WTI MAPE |
| ----- | ---------- | ---------- | -------- | -------- |
| RNN   | 2.08       | 1.99%      | 2.18     | 2.21%    |
| LSTM  | 9.39       | 10.80%     | 4.37     | 5.02%    |
| GRU   | 11.32      | 13.33%     | 3.72     | 4.26%    |

### Key Finding

Unexpectedly, the Simple RNN significantly outperformed both LSTM and GRU models under the tested experimental setup.

The results suggest that:

* Short-term market patterns dominated the dataset
* Simpler architectures generalized better
* More complex recurrent architectures may have overfitted noisy financial signals

---

# Visualizations

The project includes:

* Validation loss comparison plots
* Actual vs predicted Brent price charts
* Actual vs predicted WTI price charts

---

# Project Structure

```bash
├── notebooks/
│   └── STAT_303_Final_Project.ipynb
│
├── report/
│   └── Final_Project_Paper.pdf
│
├── slides/
│   └── Final_Presentation_Slides.pdf
│
├── figures/
│   └── plots_and_visualizations
│
└── README.md
```

---

# Technologies Used

* Python
* TensorFlow / Keras
* Scikit-Learn
* NumPy
* Pandas
* Matplotlib

---

# Limitations

This study has several limitations:

* Only a single dataset was used
* Hyperparameter tuning was limited
* No walk-forward or cross-validation techniques were implemented
* Only selected geopolitical and financial indicators were included

Future work could explore:

* Transformer-based forecasting models
* Hybrid CNN-RNN architectures
* Larger datasets
* Additional macroeconomic indicators

---

# Conclusion

This project demonstrates that more complex deep learning architectures do not always guarantee superior forecasting performance.

Under this experimental setup, the Simple RNN achieved the best predictive accuracy for multivariate oil price forecasting, outperforming both LSTM and GRU models.

---

# Authors

* Htet Khant Linn
* May Mon Thant
* Ming Thet Paing

---

# Course Information

**STAT 303**
Parami University
Professor Si Thu Aung

---

# References

* Kaggle Dataset:
  Global Oil Prices and Geopolitical Events Dataset

* TensorFlow Documentation:
  [https://www.tensorflow.org/](https://www.tensorflow.org/)

* Scikit-Learn Documentation:
  [https://scikit-learn.org/](https://scikit-learn.org/)
