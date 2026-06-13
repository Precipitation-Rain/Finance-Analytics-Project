# 💰 Finance Analytics Dashboard

A complete end-to-end financial analytics project built on 50,069 bank transactions and 5,000 customers — covering executive KPIs, customer segmentation, transaction failure intelligence, and channel performance analysis across a 5-page Power BI dashboard, Python EDA, and a machine learning churn prediction model.

![PowerBI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189ABE?style=flat)
![Domain](https://img.shields.io/badge/Domain-Banking%20%26%20Finance-darkgreen?style=flat)

---

## 📹 Dashboard Demo

<a href="YOUR_YOUTUBE_LINK_HERE">
  <img src="https://img.shields.io/badge/▶%20Watch%20Full%20Demo-Check%20it%20out-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/>
</a>

---

## 📌 Project Overview

Built to answer 5 distinct business questions that a banking analytics team actually tracks:

| # | Business Question | Dashboard Page |
|---|---|---|
| 1 | How is the business performing overall? | Executive Overview |
| 2 | What are the individual transaction details? | Drill-Down Grid |
| 3 | Who are the most and least valuable customers? | RFM Segmentation |
| 4 | Where are we losing money and why? | Failure Analysis |
| 5 | Which channels drive value and which need fixing? | Channel Intelligence |

Followed a professional BI delivery workflow throughout:

```
Business Requirements → Python EDA → Power BI (5 pages) → Python ML → Churn Model Deployment
```

---

## 🗺️ Project Architecture

```
Finance-Analytics-Project/
│
├── Part 1 — Power BI Dashboard (5 pages)
│   ├── Page 1: Executive Overview          [Guided]
│   ├── Page 2: Drill-Down Grid View        [Guided]
│   ├── Page 3: RFM Customer Intelligence   [Original]
│   ├── Page 4: Failure Analysis            [Original]
│   └── Page 5: Channel Intelligence        [Original]
│
├── Part 2 — Python Deep EDA
│   └── Finance.ipynb
│
└── Part 3 — Churn Prediction ML Model
    └── churn_model.ipynb + Streamlit app
```

> Pages 3, 4, 5 and Parts 2–3 are original work not part of the guided project.

---

## 📊 Page 1 — Executive Overview

**KPIs (with YoY comparison):** Total Amount · Total Transactions · Average Transaction Value · Total Fees · Total Tax

**Charts:**

| Visual | Type | Purpose |
|---|---|---|
| Total Amount by Month | Line Chart | Seasonal trends and spikes |
| Transaction Status | Donut | Success vs Failed vs Pending |
| Amount by Customer Segment | Bar | Retail, Premium, SME, Corporate, Wealth |
| Amount by State | Bar | Regional performance |
| Transaction Type Breakdown | Matrix | 10 types — amount, fees, tax, count |
| Amount by Gender | Donut | Male vs Female split |

**Filters:** Year · Dynamic Measure · Occupation · Category

---

## 📋 Page 2 — Drill-Down Grid View

Tabular drill-down from summary KPIs to individual transaction records in one click.

---

## 🧠 Page 3 — RFM Customer Intelligence *(Original)*

> *"Who are your most valuable customers?"*

**What is RFM?**

Each customer is scored 1–4 on Recency (how recently they transacted), Frequency (how often), and Monetary (how much). Combined score (max 12) assigns a segment.

**Segmentation Results:**

| Segment | Customers | Share | Avg Spend |
|---|---|---|---|
| Champion | 1,132 | 28.5% | ₹1,78,460 |
| Loyal | 902 | 22.7% | ₹1,03,293 |
| Potential Loyalist | 802 | 20.2% | ₹67,091 |
| At Risk | 781 | 19.6% | ₹42,509 |
| Dormant | 361 | 9.1% | ₹20,590 |

**Key Findings:**

- Champions spend **8.7× more** than Dormant customers
- Champion avg recency: 42 days vs Dormant: 448 days — scoring validated
- Retail produces 596 Champions; Wealth produces only 50 — highest income segment is underengaged
- **1,022 customers (20.4% of base) never completed a successful transaction** — dormant account problem

**How it was built:** Python script (`rfm_analysis.py`) on successful transactions only (42,921 of 50,069). Quartile binning via `pd.qcut`. Output (`rfm_segments.csv`) loaded as self-contained third table in Power BI.

---

## ⚠️ Page 4 — Failure Analysis *(Original)*

> *"Where is the business losing money and why?"*

**KPIs:**

| Metric | Value |
|---|---|
| Failed Transactions | 5,103 (10.19% failure rate) |
| Total Failed Amount | ₹4.75 Crore |
| Fraud Transactions | 632 (₹59.8L) |
| Highest Failure Type | Interest Credit — 10.80% |
| Highest Failure Channel | ATM — 10.85% |
| Most Reliable Channel | Net Banking — 9.58% |

**Charts:** Failure rate by transaction type · Failure rate by channel · Failed amount by month trend · Fraud vs genuine failure split · Failure rate by customer segment · Risk score vs transaction status

**Key Finding:** Interest Credit (bank's own auto-credit system) has the highest failure rate at 10.80% — not a customer behaviour problem but a core banking infrastructure issue.

**Notable Data Insight:** Risk score is nearly identical across Success (36.06), Failed (36.20), and Pending (36.15) transactions — the risk scoring model is not predicting transaction failure. Called out explicitly as a data quality finding.

---

## 📡 Page 5 — Channel Intelligence *(Original)*

> *"Which channels drive value, and which need fixing?"*

**KPIs:**

| Metric | Value |
|---|---|
| Total Channels | 7 |
| Highest Avg Transaction | UPI — ₹9,171 |
| Most Reliable | Net Banking — 9.58% failure |
| Highest Failure Rate | ATM — 10.85% |
| Most Used by Volume | Branch — 7,236 transactions |

**Charts:** Volume by channel · Avg transaction amount by channel · Failure rate by channel · Channel usage trend by month · Transaction type × channel matrix · Customer segment × channel matrix

**Key Finding:** UPI has the highest average transaction amount (₹9,171) — counterintuitive since UPI is typically used for small daily payments in practice. Branch remains the most-used channel despite digital alternatives — suggests older customer base or trust preference.

---

## 🔍 Part 2 — Python Deep EDA

Full exploratory analysis on the same dataset going beyond dashboard visuals.

**Covers:**
- Data quality audit — nulls, duplicates, outliers, data type corrections
- Channel whitespace cleaning (`M@bile App` → `Mobile App`)
- Statistical distributions per transaction type and customer segment
- Correlation analysis — amount, fees, tax relationships
- RFM feature engineering pipeline
- Outlier detection on transaction amounts using IQR method
- Monthly trend decomposition

**Notebook:** `Finance.ipynb`

---

## 🤖 Part 3 — Churn Prediction Model

ML model predicting which customers are at risk of stopping transactions entirely.

**Problem Definition:**
Churn label engineered from transaction data — customers with no successful transaction in 180 days classified as churned (aligned to standard banking early-warning threshold practice).

**Features used:** Recency · Frequency · Monetary · Customer Segment · State · Annual Income · Primary Channel · Primary Transaction Type

**Models trained:**
- Logistic Regression (baseline)
- Random Forest
- XGBoost (final model)

**Evaluation:** Precision · Recall · F1 · ROC-AUC

**Deployment:** Streamlit app — input customer metrics, get churn probability + risk label

---

## 🛠️ Full Tech Stack

| Layer | Tools |
|---|---|
| Business Requirements | Microsoft Word |
| Data Preparation & EDA | Python, Pandas, NumPy, Matplotlib, Seaborn |
| RFM Segmentation | Python, Pandas |
| Dashboard | Power BI Desktop |
| ML Modelling | Scikit-learn, XGBoost |
| Model Deployment | Streamlit |
| Data | CSV — customers (5K rows), transactions (50K rows), rfm_segments (3.9K rows) |

---

## 📁 Complete Project Structure

```
Finance-Analytics-Project/
│
├── Finance Analytics Dashboard.pbix   # Power BI — 5 pages
├── Finance.ipynb                       # Python EDA (Part 2)
├── rfm_analysis.py                     # RFM scoring script
├── churn_model.ipynb                   # Churn prediction model (Part 3)
├── churn_app.py                        # Streamlit deployment
├── Business Requirements.docx          # Formal requirements
├── customers.csv                       # 5,000 customer records
├── finance_transactions.csv            # 50,069 transactions (Jan 2023–Dec 2025)
├── rfm_segments.csv                    # 3,978 RFM-scored customers
└── Images/                             # Dashboard screenshots
```

---

## 🗃️ Dataset Details

**customers.csv** — 5,000 records
`customer_id · name · gender · DOB · city · state · occupation · customer_segment · annual_income`

**finance_transactions.csv** — 50,069 records · Jan 2023 – Dec 2025
`transaction_id · date · account_id · customer_id · type · channel · merchant_category · amount · fee · tax · status · is_fraud · risk_score`

**Transaction Types (10):**
Bill Payment · Card Payment · Deposit · Fee Charge · Interest Credit · Investment · Loan EMI · Refund · Transfer · Withdrawal

**Channels (7):**
Branch · UPI · ATM · Net Banking · POS · Auto Debit · Mobile App

---

## 🚀 How to Run

### Power BI Dashboard
```
1. Download Finance Analytics Dashboard.pbix
2. Open in Power BI Desktop (free)
3. If data paths break → Transform Data → Source → re-point to CSVs
```

### Python (EDA + RFM + Churn)
```bash
git clone https://github.com/Precipitation-Rain/Finance-Analytics-Project.git
cd Finance-Analytics-Project

pip install pandas numpy matplotlib seaborn scikit-learn xgboost streamlit jupyter

# Run RFM analysis
python rfm_analysis.py

# Open EDA notebook
jupyter notebook Finance.ipynb

# Open churn model notebook
jupyter notebook churn_model.ipynb

# Launch churn prediction app
streamlit run churn_app.py
```

---

## 💡 What Makes This Project Different

**Business Requirements document** — Started by defining exact KPIs and chart specs before touching any tool. This is how real BI delivery works in banking.

**3 original Power BI pages** — RFM segmentation, failure analysis, and channel intelligence were designed independently. Each answers a distinct business question banks actually monitor.

**Python → Power BI pipeline** — RFM scores computed in Python, loaded into Power BI as a third table. Tools connected, not siloed.

**Honest data finding** — Risk score shows near-identical values across Success, Failed, and Pending transactions (36.06 / 36.20 / 36.15). The risk scoring model doesn't predict transaction failure. Calling this out explicitly is what separates analysis from chart-making.

**End-to-end coverage** — Dashboard → EDA → ML model covers Data Analyst, Data Scientist, and ML Engineer skillsets in one project.

---

## 📬 Author

**Rajvardhan Shewale**

<a href="https://github.com/Precipitation-Rain">
  <img src="https://img.shields.io/badge/GitHub-Precipitation--Rain-181717?style=for-the-badge&logo=github&logoColor=white"/>
</a>
<a href="https://www.linkedin.com/in/rajvardhanshewale/">
  <img src="https://img.shields.io/badge/LinkedIn-Rajvardhan%20Shewale-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/>
</a>
<a href="https://www.kaggle.com/shambhushewale">
  <img src="https://img.shields.io/badge/Kaggle-shambhushewale-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white"/>
</a>
<a href="https://sites.google.com/view/rajvardhanshewale1771/home">
  <img src="https://img.shields.io/badge/Portfolio-Visit%20Site-4285F4?style=for-the-badge&logo=google&logoColor=white"/>
</a>

---

<a href="YOUR_YOUTUBE_LINK_HERE">
  <img src="https://img.shields.io/badge/▶%20Dashboard%20Demo-Check%20it%20out-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/>
</a>
