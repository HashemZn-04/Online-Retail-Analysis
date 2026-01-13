# Online-Retail-Analysis
Customer retention analytics: engineered RFM features from UK online retail transactions, trained/tuned classifiers (HistGB top), and built 3 actionable customer segments for targeted marketing.
# Predicting Repeat Customers & RFM Segmentation (UK Online Retail)

Customer retention analytics project using UK online retail transaction data (2010–2011).  
The project predicts repeat-purchase probability using machine learning and segments customers into actionable value groups using RFM clustering.

---

## Project Goals

- Predict which customers are likely to make a repeat purchase
- Segment customers into behavioural/value clusters
- Provide marketing recommendations for each segment
- Demonstrate an end-to-end CRISP-DM analytics workflow

---

## Dataset

**Source:** UK Online Retail Transactions (2010–2011)  
**Scope:** UK customers only  
**Granularity:** Transaction-level invoices (InvoiceNo, Quantity, UnitPrice, InvoiceDate, CustomerID, etc.)

**Cleaning steps:**
- Dropped rows with missing `CustomerID` (~27%)
- Removed returns, cancellations, and non-positive prices
- Engineered customer-level features using RFM methodology

---

## Feature Engineering

Customer-level features were engineered using:

- **Recency** – time since last purchase  
- **Frequency** – number of purchases  
- **Monetary** – total spend  
- Additional ratio and descriptive features to better capture purchasing behaviour

---

## Modelling

Six classification models were trained and tuned using cross-validated grid search:

| Model | Purpose |
|-----|-------|
| Logistic Regression | Interpretable baseline |
| Decision Tree | Non-linear rules |
| Random Forest | Robust ensemble |
| k-Nearest Neighbours | Local similarity |
| XGBoost | Gradient boosting |
| **Histogram Gradient Boosting (HistGB)** | **Best performing model** |

**Primary metric:** F1 Score  
**Best Model:** **HistGB**

| Metric | HistGB |
|------|------|
| F1 Score | ~0.83 |
| ROC-AUC | ~0.84 |

---

## Customer Segmentation (K-Means)

K-means clustering on standardized RFM features found **3 distinct segments**:

| Segment | Description | % Customers | % Revenue |
|--------|-----------|-----------|----------|
| High-Value Active | Frequent, high spenders | 14.85% | 54.71% |
| Mid-Value Occasional | Largest group, low repeat rate | 46.12% | 38.87% |
| Low-Value | Low spenders, higher repeat than mid-value | 39.03% | 6.42% |

---

## Business Recommendations

| Segment | Strategy |
|-------|---------|
| **High-Value** | VIP programs, exclusive offers, upsell new products |
| **Mid-Value** | Bundles, promotions to increase frequency |
| **Low-Value** | Low-cost email/SMS, selective win-back targeting |

**Model Threshold Tuning (HistGB):**
- High-Value: Low threshold (maximize recall)
- Mid-Value: Balanced threshold
- Low-Value: High threshold (maximize precision)

---

## Repository Structure

```text
uk-online-retail-repeat-customers/
  34074759_code.ipynb
  README.md
  report/
    34074759_coursework.docx
    34074759_presentation.pptx
  requirements.txt
