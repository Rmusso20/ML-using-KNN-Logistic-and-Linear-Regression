[README.md](https://github.com/user-attachments/files/29073189/README.md)# Electricity Price Prediction — KNN, Logistic & Linear Regression

Predicting electricity prices in New South Wales (NSW) using the [Electricity Demands dataset](https://www.kaggle.com/) from Kaggle. The project compares **KNN Regression** for continuous price forecasting and **KNN vs. Logistic Regression** for classifying whether the price goes UP or DOWN.

---

## Dataset

**`electricity.csv`** — sourced from Kaggle. Each row represents a 30-minute interval with the following features:

| Column | Description |
|---|---|
| `day` | Day of the week |
| `period` | Time of day (normalized) |
| `nswprice` | Electricity price in NSW *(target for regression)* |
| `nswdemand` | Electricity demand in NSW |
| `vicprice` | Electricity price in Victoria |
| `vicdemand` | Electricity demand in Victoria |
| `transfer` | Power transfer between regions |
| `class` | Price direction: UP or DOWN *(target for classification)* |

---

## Project Structure

```
├── Electrical_project.ipynb   # Main notebook
└── README.md
```

---

## What's Inside the Notebook

### Part 1 — KNN Regression
- Loads and cleans the dataset (parses `day` encoding)
- Splits into train/test sets and applies **MinMaxScaler**
- Tunes `k` from 1–20 using 5-fold cross-validation (RMSE)
- Evaluates the best model on the test set (RMSE, R²)
- Forecasts a future NSW price given a new input example

### Part 2 — Classification: Logistic Regression vs. KNN
- Creates a binary label from the `class` column (UP→1, DOWN→0)
- Trains and compares three classifiers:
  - **Logistic Regression** (standard)
  - **Logistic Regression** (class-weight balanced)
  - **KNN Classifier** (k=4)
- Final comparison table: Accuracy, Precision, Recall, F1-score

---

## Results Summary

| Model | Task | Metric |
|---|---|---|
| KNN Regressor (best k) | Price prediction | RMSE / R² on test set |
| Logistic Regression | UP/DOWN classification | Accuracy / F1 |
| Logistic Regression (balanced) | UP/DOWN classification | Accuracy / F1 |
| KNN Classifier (k=4) | UP/DOWN classification | Accuracy / F1 |

*(Run the notebook to see exact values — they depend on the dataset split.)*

---

## Setup

```bash
pip install pandas scikit-learn matplotlib seaborn
```

Then open the notebook:

```bash
jupyter notebook Electrical_project.ipynb
```

> **Note:** Place `electricity.csv` at `/content/sample_data/electricity.csv` (Google Colab default) or update the `filepath` variable in the first code cell to match your local path.

---

## Tech Stack

- Python 3
- pandas, NumPy
- scikit-learn (KNeighborsRegressor, KNeighborsClassifier, LogisticRegression)
- Matplotlib, Seaborn

