# Phishing URL Detection with Logistic Regression and SHAP

Lab 1 for M115 (AI & Intelligent Systems), Master in Intelligent Systems and Cyber Defense, ENSIASD Taroudant, Ibn Zohr University.

## What this does

Trains and explains a logistic regression model that classifies URLs as phishing or legitimate, using the PhiUSIIL Phishing URL Dataset (235,795 URLs, 56 features).

## Steps

1. **EDA**: check data quality, class balance, feature distributions and correlations.
2. **Preprocessing**: 75/25 stratified split, then standardize using training data only (no data leakage).
3. **Modeling**: compare 5 logistic regression setups (no regularization, L2 strong/standard, L1, class-weighted) and look at the L1 regularization path.
4. **Explainability**: use weights, odds ratios and SHAP (global and per-URL) to see what drives predictions.
5. **Threshold analysis**: compare thresholds 0.20, 0.50 and 0.85 for different SOC uses.

## Important note on labels

In the raw dataset, `label = 1` means legitimate and `label = 0` means phishing. The notebook flips this into `IsPhishing` (1 = phishing) so recall and precision measure attack detection.

## Key results

- All models score above 0.99 F1 on the test set.
- L1 (C=0.01) removes 24 of 49 features with almost no loss in F1.
- Top phishing signals: high letter/digit/special-character ratios in the URL.
- Top legitimate signals: HTTPS, JavaScript files, internal links, social links.
- Threshold 0.20 catches more phishing, 0.85 gives zero false alarms.

## How to run

1. Download `PhiUSIIL_Phishing_URL_Dataset.csv` from [Kaggle](https://www.kaggle.com/datasets/kaggleprollc/phishing-url-websites-dataset-phiusiil/data).
2. Open `M115_Lab1.ipynb` in Google Colab (or Jupyter).
3. Upload the CSV when prompted (or adjust the path).
4. Run all cells.

## Requirements

`numpy`, `pandas`, `matplotlib`, `seaborn`, `scikit-learn`, `shap`

## Dataset reference

Prasad & Chandra, *Computers & Security*, 2024.
