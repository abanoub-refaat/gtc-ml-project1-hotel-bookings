# GTC ML Project 1 - Data Cleaning & Preprocessing Challenge

This project is part of the **GTC Machine Learning Track** and focuses on building a **robust data preprocessing pipeline** for the hotel booking dataset.

The goal is not to build the final predictive model but to prepare the raw dataset for machine learning. High-quality preprocessing will directly influence the success of future models that aim to predict booking cancellations.

---

## 📌 Project Overview

The **Revenue Team** has identified that last-minute booking cancellations significantly impact profitability. To support cancellation prediction models, this project focuses on:

- Exploring and understanding the raw dataset.
- Identifying and addressing **data quality issues** (missing values, outliers, duplicates, incorrect data types).
- Creating new, meaningful features.
- Encoding categorical variables for ML readiness.
- Preparing a **clean and structured dataset** ready for training/testing.

---

## 📂 Dataset

- **File:** `hotel_bookings.csv`
- **Source:** Provided via the Property Management System (PMS).
- **Size:** \~119K rows, 32 columns.
- **Target (for future modeling):** Booking cancellation flag.

---

## ⚙️ Preprocessing Pipeline

The data cleaning and preprocessing steps include:

### 1. Data Exploration

- Loaded dataset into Pandas DataFrame.
- Generated **summary statistics** (`.describe()`, `.info()`).
- Visualized **missing values** using `missingno` and heatmaps.

### 2. Handling Missing Data

- `company` & `agent`: Replaced missing values with `"None"` or `0`.
- `country`: Imputed with **mode** or `"Unknown"`.
- `children`: Imputed with **median**.

### 3. Handling Duplicates

- Removed exact duplicate rows.

### 4. Outlier Detection & Treatment

- Used **boxplots** and **IQR method** for numerical columns (`adr`, `lead_time`).
- Applied **capping** (e.g., `adr > 1000 → 1000`).

### 5. Feature Engineering

- `total_guests = adults + children + babies`
- `total_nights = stays_in_weekend_nights + stays_in_week_nights`
- `is_family` → Binary flag (`Yes/No`) if booking includes children/babies.

### 6. Data Type Fixes

- Converted date columns to proper datetime format.

### 7. Encoding Categorical Variables

- Low-cardinality features → **One-Hot Encoding** (`meal`, `market_segment`).
- High-cardinality (`country`) → **frequency encoding** or grouping rare categories as `"Other"`.

### 8. Data Leakage Prevention

- Dropped `reservation_status` and `reservation_status_date` (information not available at prediction time).

### 9. Final Split

- Train/Test split (`test_size=0.2`, `random_state=42`).

---

## 📊 Tools & Libraries

- **Python 3.10+**
- **Google Colab** (workspace)
- **Pandas** (data manipulation)
- **NumPy** (numerical operations)
- **Matplotlib / Seaborn** (visualization)
- **Missingno** (missing data visualization)
- **Scikit-learn** (encoding, splitting)

---

## 📁 Repository Structure

```
gtc-ml-project1-hotel-bookings/
│── hotel_bookings.csv       # Raw dataset
│── GTC_Project1.ipynb       # Jupyter/Colab notebook with full pipeline
│── README.md                # Project documentation
```

---

## 🚀 How to Run

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/gtc-ml-project1-hotel-bookings.git
   cd gtc-ml-project1-hotel-bookings
   ```

2. Open the notebook in **Google Colab**.

3. Upload the dataset (`hotel_bookings.csv`) if required.

4. Run all cells to reproduce the preprocessing pipeline.

---

## ✨ Key Learnings

- Real-world datasets often contain **missing values, duplicates, outliers, and inconsistent formats**.
- Careful preprocessing ensures **robust and reliable models** downstream.
- Feature engineering and encoding strategies directly impact model interpretability and performance.

---

## 📌 Next Steps

- Train ML models (e.g., Logistic Regression, Random Forest, XGBoost) on the cleaned dataset.
- Evaluate model performance in predicting cancellations.
- Experiment with **scaling** and **feature selection** techniques.

---

## 📜 License

This project is for **educational purposes** under the GTC ML Track.
