# Customer Churn Prediction

## 📌 Business Problem
A telecom company wants to identify customers likely to churn so that retention teams can proactively engage them.  
This project builds an end‑to‑end machine learning solution to predict churn using the IBM Telco Customer Churn dataset.

---

## ✅ Achievements (per assignment requirements)

1. **Data Understanding & Preparation**
   - Loaded and explored dataset (7,043 records, 21 columns).
   - Handled missing values in `TotalCharges` (11 blanks → median imputation).
   - Dropped unnecessary identifier (`customerID`).
   - Converted target variable `Churn` to numeric (Yes=1, No=0).
   - Train/Test split (70:30, `random_state=42`).

2. **Exploratory Data Analysis (EDA)**
   - Visualized churn distribution, contract type, tenure, monthly charges, internet service, and payment method.
   - Derived business insights (e.g., higher churn among month‑to‑month contracts, fiber optic users, electronic check payments).

3. **Feature Engineering**
   - **ServiceCount**: Number of value‑added services subscribed.
   - **AvgMonthlySpend**: TotalCharges ÷ tenure (or MonthlyCharges if tenure=0).

4. **Model Development**
   - Built two Decision Tree Classifiers:
     - **Model 1**: Baseline (max_depth=3).
     - **Model 2**: Tuned (max_depth=6, min_samples_split=10).
   - Compared performance metrics.

5. **Model Evaluation**
   - Metrics: Accuracy, Precision, Recall, F1 Score, Confusion Matrix.
   - Model 2 selected (better recall and F1 score, critical for churn prevention).

6. **Model Interpretation**
   - Feature importance analysis (top drivers: Tenure, MonthlyCharges, Fiber Optic, SeniorCitizen, PaymentMethod).
   - Decision Tree visualization for interpretability.

7. **Model Saving & API**
   - Saved preprocessing pipeline (`model/preprocessor.pkl`) and final model (`model/churn_model.pkl`).
   - Built Flask REST API (`app.py`) with endpoint:
     - `POST /predict` → accepts JSON, applies preprocessing, returns prediction + churn probability.

---

## Video Link

https://nagarro-my.sharepoint.com/personal/jasmeet_kaur02_nagarro_com/_layouts/15/stream.aspx?id=%2Fpersonal%2Fjasmeet%5Fkaur02%5Fnagarro%5Fcom%2FDocuments%2FNAGP%5FAI%5FDS%5FVideos%2FCustomer%5FChurn%5FPrediction%5FDemo%2Emp4&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJPbmVEcml2ZUZvckJ1c2luZXNzIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXciLCJyZWZlcnJhbFZpZXciOiJNeUZpbGVzTGlua0NvcHkifX0&ga=1&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2E75fbd567%2Ddc9c%2D4bd4%2Db115%2D6fd77bc37ae2)

---

## 🚀 Setup Instructions

### 1. Clone Repository
```bash
git clone https://github.com/Jasmeet02/customer_churn_project
cd customer-churn-prediction
```

### 2. Install Dependencies
```bash
python -m venv .venv
source .venv/bin/activate   # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Run Jupyter Notebook
```bash
jupyter notebook notebook/churn_analysis.ipynb
```

### 4. Train & Save Model
Running the notebook will generate:
- `model/preprocessor.pkl`
- `model/churn_model.pkl`

### 5. Start Flask API
```bash
python app.py
```

### 6. Test the API
Open a second terminal and run:
```bash
python test_request.py
```
This sends the sample payload from `sample_request.json` to the running Flask API at `http://127.0.0.1:5000/predict`.

## Project Structure

customer_churn_project/
│── data/
│   └── TelcoCustomerChurn.csv
│── notebook/
│   └── churn_analysis.ipynb
│── model/
│   ├── preprocessor.pkl
│   └── churn_model.pkl
│── app.py
│── requirements.txt
│── README.md
│── sample_request.json
── sample_request2.json
│── test_request.py




