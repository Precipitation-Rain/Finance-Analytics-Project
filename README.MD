# 💰 Finance Analytics Dashboard — Power BI + Python

An end-to-end financial analytics project built for a banking organization — covering transaction performance, customer behaviour, fees, taxes, and regional trends across multiple business segments. Includes a formal Business Requirements document, Python EDA, a two-page guided Power BI dashboard, and an original RFM customer segmentation page built independently.

![PowerBI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Banking%20%26%20Finance-darkgreen?style=flat)
![RFM](https://img.shields.io/badge/Original%20Work-RFM%20Segmentation-blue?style=flat)

---

## 📌 Project Overview

A financial organization needed a centralized analytical solution to monitor KPIs, understand customer segment behaviour, track transaction performance, and identify high-performing regions — replacing manual reporting with an interactive, filterable dashboard.

This project follows a professional BI delivery workflow:

```
Business Requirements → Data Preparation (Python) → Power BI Dashboard → Drill-Down Grid View → RFM Segmentation (original)
```

The full requirements are documented in [`Business Requirements.docx`](./Business%20Requirements.docx).

---

## 🎯 Business Problems Solved

The management team faced challenges tracking:

- Overall transaction growth and year-over-year financial performance
- Monthly trends in transaction amounts across the year
- Successful vs failed vs pending transactions
- Customer segment contribution (Retail, Premium, SME, Corporate, Wealth)
- State-wise regional performance
- Transaction type profitability (10 types from Loan EMI to Investments)
- Gender-based customer participation
- Operational fees and tax collection efficiency
- **Which customers are most valuable — and which are about to churn** (RFM analysis)

---

## 📊 Dashboard — Page 1: Executive Overview

### KPIs (with YoY Growth)

| KPI | Description |
|---|---|
| Total Amount | Total transaction value processed, with year-over-year comparison |
| Total Transactions | Volume of transactions with yearly trend |
| Average Transaction Value | Mean amount per transaction |
| Total Fees | Aggregate fees collected |
| Total Tax | Total tax generated across all transactions |

### Charts

| Visual | Type | Purpose |
|---|---|---|
| Total Amount by Month | Line / Area Chart | Identify seasonal spikes and monthly trends |
| Transaction Status Split | Donut Chart | Success vs Failed vs Pending — measures operational efficiency |
| Amount by Customer Segment | Horizontal Bar Chart | Ranks Retail, Premium, SME, Corporate, Wealth contribution |
| Amount by State | Horizontal Bar Chart | Identifies top-performing regions |
| Transaction Type Analysis | Matrix / Heatmap | Amount, Fees, Tax, Count across 10 transaction types |
| Amount by Gender | Donut Chart | Male vs Female transaction participation |

### Dynamic Filters
Users can slice all visuals by: **Year · Dynamic Measure · Occupation · Category**

---

## 📋 Dashboard — Page 2: Drill-Down Grid View

A detailed tabular view with drill-down capability into underlying transaction records — enabling analysts to go from summary KPIs to individual data points in one click.

---

## 🧠 Dashboard — Page 3: RFM Customer Segmentation *(Original Work)*

> This page was not part of the guided project. Built independently using RFM analysis — a standard framework used by banks and fintechs to understand customer value and behaviour.

### What is RFM?

RFM segments customers based on three behavioural metrics:

| Metric | Question | Logic |
|---|---|---|
| **R — Recency** | When did they last transact? | Transacted yesterday > transacted 6 months ago |
| **F — Frequency** | How often do they transact? | 15 transactions > 2 transactions |
| **M — Monetary** | How much have they spent total? | ₹1.5L spent > ₹20K spent |

Each customer is scored 1–4 on all three metrics. Combined score (max 12, min 3) determines their segment.

### Segmentation Results (from 50,069 transactions, 5,000 customers)

| Segment | Score | Customers | Share | Avg Spend |
|---|---|---|---|---|
| Champion | 10–12 | 1,132 | 28.5% | ₹1,78,460 |
| Loyal | 8–9 | 902 | 22.7% | ₹1,03,293 |
| Potential Loyalist | 6–7 | 802 | 20.2% | ₹67,091 |
| At Risk | 4–5 | 781 | 19.6% | ₹42,509 |
| Dormant | 3 | 361 | 9.1% | ₹20,590 |

**Key finding:** Champions spend **8.7× more** than Dormant customers. The business action: retain Champions, re-engage the 781 At Risk customers before they go Dormant.

### How RFM Was Calculated

RFM scores were computed in Python (`rfm_analysis.py`) on **successful transactions only** (42,921 out of 50,069). Negative amounts (refunds) were excluded from Monetary scoring. Scores were assigned using quartile-based binning (`pd.qcut`) to ensure equal distribution across segments. The output (`rfm_segments.csv`) was loaded into Power BI as a third table and joined to the transaction data on `customer_id`.

### Page 3 Visuals

| Visual | Purpose |
|---|---|
| Segment distribution donut | How customers split across 5 segments |
| Avg spend by segment | Shows the 8.7× spend gap Champion vs Dormant |
| Avg recency by segment | Shows how recently each segment transacted |
| Customer segment × RFM segment matrix | Do Champions come from Wealth or Retail customers? |
| At Risk KPI card | 781 customers — the urgent business action number |

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data Preparation & EDA | Python, Pandas, Jupyter Notebook |
| RFM Segmentation | Python, Pandas (`rfm_analysis.py`) |
| Dashboard & Visualisation | Power BI Desktop |
| Data Storage | CSV (customers + transactions + rfm_segments) |
| Requirements Documentation | Microsoft Word (.docx) |

---

## 📁 Project Structure

```
Finance-Analytics-Project/
│
├── Finance.ipynb                    # Python EDA — data cleaning, profiling, exploration
├── rfm_analysis.py                  # RFM scoring script (original work)
├── Finance Analytics Dashboard.pbix # Power BI dashboard (3 pages)
├── Business Requirements.docx       # Formal requirements document
├── customers.csv                    # Customer master data
├── finance_transactions.csv         # Transaction records
├── rfm_segments.csv                 # RFM output — 3,978 customers scored and segmented
└── Images/                          # Dashboard screenshots
```

---

## 🗃️ Dataset

**customers.csv** — Customer master records
- Fields: Customer ID, Name, Gender, Age, State, Occupation, Customer Segment (Retail / Premium / SME / Corporate / Wealth)

**finance_transactions.csv** — Transaction records
- Fields: Transaction ID, Customer ID, Date, Transaction Type, Amount, Fees, Tax, Status (Success / Failed / Pending)
- 50,069 records · Date range: Jan 2023 – Dec 2025

**Transaction Types covered:**
Bill Payment · Card Payment · Deposit · Fee Charge · Interest Credit · Investment · Loan EMI · Refund · Transfer · Withdrawal

---

## 🚀 How to Use

### Power BI Dashboard
1. Download `Finance Analytics Dashboard.pbix`
2. Open in **Power BI Desktop** (free download from Microsoft)
3. If data paths break, re-point to the CSVs via Transform Data → Source

### Python EDA + RFM
```bash
# 1. Clone the repo
git clone https://github.com/Precipitation-Rain/Finance-Analytics-Project.git
cd Finance-Analytics-Project

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Run RFM analysis
python rfm_analysis.py
# Outputs: rfm_segments.csv (3,978 customers with R, F, M scores and segment labels)

# 4. Open EDA notebook
jupyter notebook Finance.ipynb
```

---

## 💡 What Makes This Project Different

**Business Requirements document** — Most student BI projects jump straight to building. This project started by defining the exact KPIs, chart types, and filter requirements in a formal document — exactly how real BI delivery works in banking and financial services.

**Original RFM page** — Page 3 was not part of the guided project. RFM is a real industry framework used by every major bank and fintech. Computing it in Python and feeding it into Power BI as a third analytical layer shows end-to-end thinking beyond the dashboard brief.

**Two-dataset join model** — Joining customer demographics with transaction records simulates the relational data that analysts work with daily at banks and NBFCs.

**10 transaction type breakdown** — Going beyond totals to break down by category (Loan EMI, Investments, Refunds, etc.) is the granularity financial stakeholders actually need.

---

## 📬 Author

**Rajvardhan Shewale**
- [GitHub](https://github.com/Precipitation-Rain)
- [LinkedIn](https://www.linkedin.com/in/rajvardhanshewale/)
- [Kaggle](https://www.kaggle.com/shambhushewale)
- [Portfolio](https://sites.google.com/view/rajvardhanshewale1771/home)