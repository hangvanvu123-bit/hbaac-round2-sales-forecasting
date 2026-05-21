# HBAAC Round 2 - Sales Forecasting Baseline

## Introduction

This project is a baseline solution for the HBAAC Round 2 forecasting competition.

The objective is to forecast future product sales quantities for each SKU based on historical transaction data.

The notebook performs:
- Data loading
- Data cleaning
- Feature preprocessing
- Daily sales aggregation
- Baseline forecasting using the last 28-day average sales

---

## Dataset

Dataset provided by the competition organizer.

Files used:
- `train.csv`
- `sample_submission.csv`

Main columns:
- `Date`
- `ItemCode`
- `Quantity`
- `UnitPrice`
- `SalesAmount`
- `Unit Cost`
- `Cost Amount`

---

## Data Preprocessing

The following preprocessing steps were applied:

### 1. Convert Date Column
```python
train['Date'] = pd.to_datetime(train['Date'])
```

### 2. Clean Numeric Columns
Some numeric columns used commas instead of decimal points.

Converted:
- `UnitPrice`
- `Unit Cost`
- `Cost Amount`

to numeric format.

### 3. Handle Negative Quantity
Negative quantities were clipped to zero.

```python
train['Quantity'] = train['Quantity'].clip(lower=0)
```

### 4. Aggregate Daily Sales
Sales were aggregated by:
- Date
- ItemCode

to create daily demand per SKU.

---

## Forecasting Method

A simple baseline forecasting approach was used.

### Last 28-Day Mean Forecast

Steps:
1. Take the latest 28 days of sales data
2. Calculate average daily quantity for each SKU
3. Use that average value to forecast the next 28 days

Formula:

Forecast(SKU) = Mean quantity over last 28 days

This prediction is repeated for:
- F1
- F2
- ...
- F28

---

## Libraries Used

- NumPy
- Pandas

---

## Output

The notebook generates:

```text
submission.csv
```

which follows the competition submission format.

---

## Project Structure

```text
├── notebook.ipynb
├── README.md
└── submission.csv
```

---

## How to Run

1. Upload competition dataset to Kaggle
2. Open notebook
3. Run all cells
4. Download `submission.csv`

---

## Notes

This project is a simple baseline model intended for experimentation and further improvement.

Possible future improvements:
- Time series models
- XGBoost / LightGBM
- Feature engineering
- Seasonal trend extraction
- Deep learning forecasting models

---

## Author

deadline
# repo
