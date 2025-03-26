# Credit Risk Modeling & Strategy Project

This project builds a credit risk model and defines strategic credit assignment thresholds to optimize revenue while minimizing default risk.

---

## 📊 Problem Statement

Using customer data from the AMEX Default Prediction competition, we aim to:
- Predict customer default using historical behavior
- Engineer features over time for better predictive accuracy
- Evaluate model performance using XGBoost and Neural Networks
- **Design business strategies based on predicted default probabilities**

---

## 📁 Dataset

- Source: [AMEX Default Prediction - Kaggle](https://www.kaggle.com/competitions/amex-default-prediction/data)
- `train_labels.csv`: Contains default status as of April 2018
- `train_data.csv`: Contains customer activity from April 2017 to April 2018

---

## 🧪 Key Steps

1. **Data Sampling & Merging**  
   Sampled 20% of `train_labels.csv` and merged with customer activity data

2. **Feature Engineering**  
   Aggregated numerical and categorical features across different time windows (6-month avg, April 2018 snapshot, etc.)

3. **One-Hot Encoding & Data Processing**  
   - One-hot encoded categorical variables  
   - Standardized numerical features  
   - Handled missing values and outliers

4. **Modeling**  
   - Trained and tuned XGBoost and Neural Networks using extensive grid search  
   - Evaluated models on AUC across Train, Test1, and Test2 sets  
   - Selected the best model based on generalizability and performance metrics

---

## 📈 Strategy Design & Business Impact

The final model outputs a probability of default (PD) for each customer. Based on this PD, we designed two business strategies:

- **Conservative Strategy**: Lowers the risk threshold by approving only customers with very low predicted PD  
  → Lower default rate, lower revenue, safer portfolio

- **Aggressive Strategy**: Allows customers with higher predicted PD to be approved  
  → Higher revenue potential, but increased default risk

For each strategy:
- We calculated the **portfolio-level default rate**
- We estimated **monthly and annual expected revenue** using historical balance (B_) and spend (S_) features  
- Revenue formula includes:
  - 0.1% fee on spend  
  - 2% monthly interest on unpaid balance  
  - Revenue = (0.001 × Spend) + (0.02 × Balance)

We wrote a function to estimate **default rate and revenue given any threshold**, and compared strategies under the constraint:  
**Default rate should not exceed 10%**

Final recommendation was made based on a tradeoff between risk tolerance and potential gain.

---

## 🚀 Final Deliverables

- Trained Models (XGBoost, NN)
- SHAP Interpretability Visuals
- Feature Importance CSVs
- Grid Search Result Tables
- Strategy Simulator Function
- Conservative vs. Aggressive Strategy Comparison

---

## 🛠️ Tech Stack

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- TensorFlow/Keras
- SHAP
- Matplotlib, Seaborn, Plotly

---

## 📦 Setup Instructions

1. Clone the repo
2. Create a virtual environment (optional)
3. Install dependencies:

```bash
pip install -r requirements.txt
