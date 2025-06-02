# codealpha_tasks_01

# 🏦 Credit Scoring Model

This project uses machine learning to predict whether a customer will be approved for credit based on historical financial and demographic data.

---

## 📁 Files

| File                      | Description                                          |
| ------------------------- | ---------------------------------------------------- |
| `cc_approvals.data`       | Raw dataset with features and approval status        |
| `credit_scoring_model.py` | Python code for training, evaluating, and predicting |
| `encoders.pkl`            | Saved label encoders for categorical variables       |
| `model.pkl`               | Trained Random Forest or Decision Tree model         |
| `README.md`               | Project overview and instructions                    |

---

## 📊 Dataset Description

The dataset contains anonymized financial and demographic features. Each row represents a customer, and the target label indicates whether their credit was approved (`1`) or not (`0`).

### 📌 Features:

| Feature            | Type            | Description                        |
| ------------------ | --------------- | ---------------------------------- |
| Gender             | Categorical     | 'a', 'b'                           |
| Age                | Numerical       | Years                              |
| Debt               | Numerical       | Amount owed                        |
| Married            | Categorical     | Marital status                     |
| BankCustomer       | Categorical     | Existing bank customer?            |
| EducationLevel     | Categorical     | Education background               |
| Ethnicity          | Categorical     | Ethnic group                       |
| YearsEmployed      | Numerical       | Years of employment                |
| PriorDefault       | Categorical     | Had previous default? (t/f)        |
| Employed           | Categorical     | Currently employed? (t/f)          |
| CreditScore        | Numerical       | Credit score estimate              |
| DriversLicense     | Categorical     | Has driver's license? (t/f)        |
| Citizen            | Categorical     | Citizenship status                 |
| ZipCode            | Numerical       | Zip code (not used for prediction) |
| Income             | Numerical       | Annual income                      |
| **ApprovalStatus** | Binary (Target) | 1 = Approved, 0 = Denied           |

---

## 🔧 Preprocessing Steps

* Replaced missing values represented by `?`

  * Categorical: replaced with **mode**
  * Numerical: replaced with **mean**
* Encoded categorical features using `LabelEncoder`

  * One encoder saved per categorical column
* Standardized column order and removed unnecessary fields (e.g., ZipCode)

---

## 🤖 Model Training

Used **Random Forest** or **Decision Tree** classifier from `scikit-learn`.

### Metrics Evaluated:

* Accuracy
* Confusion Matrix
* Classification Report (Precision, Recall, F1)

---

## 🔮 Predicting a New Customer

To predict credit approval for a new customer:

1. Prepare a dictionary of raw input values (like `'a'`, `'t'`, etc.).
2. Load saved encoders and model.
3. Preprocess input using the **same encoders**.
4. Align feature columns and predict.

### Example:

```python
new_customer = {
    "Gender": "a",
    "Age": 30,
    "Debt": 2.5,
    "Married": "u",
    "BankCustomer": "g",
    "EducationLevel": "q",
    "Ethnicity": "v",
    "YearsEmployed": 1.5,
    "PriorDefault": "f",
    "Employed": "t",
    "CreditScore": 10.0,
    "DriversLicense": "t",
    "Citizen": "g",
    "ZipCode": 0,
    "Income": 10000
}
```

Run the script or use a helper function to return:

```
✅ Credit Approved
```

or

```
❌ Credit Not Approved
```
