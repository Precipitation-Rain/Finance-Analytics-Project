# 💰 Finance Analytics Dashboard — Power BI + Python

An end-to-end financial analytics project built for a banking organization — covering transaction performance, customer behaviour, fees, taxes, and regional trends across multiple business segments. Includes a formal Business Requirements document, Python EDA, a two-page guided Power BI dashboard, and an original RFM customer segmentation page built independently.

![PowerBI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Banking%20%26%20Finance-darkgreen?style=flat)
![RFM](https://img.shields.io/badge/Original%20Work-RFM%20Segmentation-blue?style=flat)

---

## 📹 Dashboard Demo

<a href="YOUR_YOUTUBE_LINK_HERE">
  <img src="https://img.shields.io/badge/▶️ Watch Demo-Check it out-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/>
</a>

> Replace `YOUR_YOUTUBE_LINK_HERE` with your YouTube Unlisted link after recording.

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

- Overall transaction growth and year-over-year financial performance
- Monthly trends in transaction amounts across the year
- Successful vs failed vs pending transactions
- Customer segment contribution (Retail, Premium, SME, Corporate, Wealth)
- State-wise regional performance
- Transaction type profitability (10 types from Loan EMI to Investments)
- Gender-based customer participation
- Operational fees and tax collection efficiency
- **Which customers are most valuable — and which are about to churn** (RFM, Page 3)

---

## 📊 Dashboard — Page 1: Executive Overview

### KPIs (with YoY Growth)

| KPI | Description |
|---|---|
| Total Amount | Total transaction value with year-over-year comparison |
| Total Transactions | Volume of transactions with yearly trend |
| Average Transaction Value | Mean amount per transaction |
| Total Fees | Aggregate fees collected |
| Total Tax | Total tax generated across all transactions |

### Charts

| Visual | Type | Purpose |
|---|---|---|
| Total Amount by Month | Line / Area Chart | Seasonal spikes and monthly trends |
| Transaction Status Split | Donut Chart | Success vs Failed vs Pending |
| Amount by Customer Segment | Horizontal Bar Chart | Retail, Premium, SME, Corporate, Wealth contribution |
| Amount by State | Horizontal Bar Chart | Top-performing regions |
| Transaction Type Analysis | Matrix / Heatmap | Amount, Fees, Tax, Count across 10 transaction types |
| Amount by Gender | Donut Chart | Male vs Female transaction participation |

**Dynamic Filters:** Year · Dynamic Measure · Occupation · Category

---

## 📋 Dashboard — Page 2: Drill-Down Grid View

Detailed tabular view with drill-down into individual transaction records — from summary KPIs to raw data in one click.

---

## 🧠 Dashboard — Page 3: RFM Customer Intelligence *(Original Work)*

> This page was not part of the guided project. Built independently using RFM — a standard framework used by banks and fintechs to understand customer value and predict churn.

*"Who are your most valuable customers?"*

### What is RFM?

| Metric | Question | Logic |
|---|---|---|
| **R — Recency** | When did they last transact? | Transacted recently = higher score |
| **F — Frequency** | How often do they transact? | More transactions = higher score |
| **M — Monetary** | How much have they spent total? | Higher spend = higher score |

Each customer scored 1–4 on all three. Combined score (max 12, min 3) determines segment.

### Segmentation Results

| Segment | Score | Customers | Share | Avg Spend |
|---|---|---|---|---|
| Champion | 10–12 | 1,132 | 28.5% | ₹1,78,460 |
| Loyal | 8–9 | 902 | 22.7% | ₹1,03,293 |
| Potential Loyalist | 6–7 | 802 | 20.2% | ₹67,091 |
| At Risk | 4–5 | 781 | 19.6% | ₹42,509 |
| Dormant | 3 | 361 | 9.1% | ₹20,590 |

**Key Finding 1:** Champions spend **8.7× more** than Dormant customers.

**Key Finding 2:** Avg recency — Champion: 42 days vs Dormant: 448 days. Scoring validated.

**Key Finding 3 (from matrix):** Retail produces the most Champions (596) despite being a mass-market segment. Wealth produces only 50 Champions — the bank is underengaging its highest-income customers. Actionable insight for the business.

**Key Finding 4:** 1,022 customers (20.4% of total base) never completed a successful transaction — a dormant account problem the business needs to address.

### Page 3 Charts

| Visual | Purpose |
|---|---|
| Customers by Segment (Donut) | How customers split across 5 segments |
| Avg Spend by Segment (Bar) | Shows the 8.7× spend gap |
| Avg Recency by Segment (Bar) | Validates scoring — Champions transacted most recently |
| RFM Segment × Customer Segment (Matrix) | Which customer types produce Champions |
| Customers by Transaction Count (Column) | Distribution of how often customers transact |
| RFM Score Distribution (Column) | How scores cluster — most customers are mid-tier |

### How RFM Was Calculated

Computed in Python (`rfm_analysis.py`) on **successful transactions only** (42,921 of 50,069). Negative amounts (refunds) excluded from Monetary. Scores assigned via quartile binning (`pd.qcut`). Output (`rfm_segments.csv`) loaded into Power BI as a third table — self-contained, no relationship dependency on other tables.

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data Preparation & EDA | Python, Pandas, Jupyter Notebook |
| RFM Segmentation | Python, Pandas (`rfm_analysis.py`) |
| Dashboard & Visualisation | Power BI Desktop |
| Data | CSV — customers, transactions, rfm_segments |
| Requirements | Microsoft Word (.docx) |

---

## 📁 Project Structure

```
Finance-Analytics-Project/
│
├── Finance.ipynb                     # Python EDA — cleaning, profiling, exploration
├── rfm_analysis.py                   # RFM scoring script (original work)
├── Finance Analytics Dashboard.pbix  # Power BI dashboard (3 pages)
├── Business Requirements.docx        # Formal requirements document
├── customers.csv                     # Customer master data (5,000 records)
├── finance_transactions.csv          # Transaction records (50,069 records)
├── rfm_segments.csv                  # RFM output — 3,978 customers scored
└── Images/                           # Dashboard screenshots
```

---

## 🗃️ Dataset

**customers.csv** — 5,000 customer records
- Customer ID, Name, Gender, DOB, City, State, Occupation, Segment, Annual Income

**finance_transactions.csv** — 50,069 transaction records · Jan 2023 – Dec 2025
- Transaction ID, Customer ID, Date, Type, Amount, Fees, Tax, Status, Channel, Merchant Category

**Transaction Types:**
Bill Payment · Card Payment · Deposit · Fee Charge · Interest Credit · Investment · Loan EMI · Refund · Transfer · Withdrawal

---

## 🚀 How to Run

### Power BI Dashboard
1. Download `Finance Analytics Dashboard.pbix`
2. Open in **Power BI Desktop** (free)
3. If paths break → Transform Data → Source → re-point to CSVs

### Python EDA + RFM
```bash
git clone https://github.com/Precipitation-Rain/Finance-Analytics-Project.git
cd Finance-Analytics-Project

pip install pandas numpy matplotlib seaborn jupyter

# Run RFM analysis — outputs rfm_segments.csv
python rfm_analysis.py

# Open EDA notebook
jupyter notebook Finance.ipynb
```

---

## 💡 What Makes This Project Different

**Business Requirements document** — Project started with a formal requirements doc defining KPIs, charts, and filters before any tool was opened. This is how real BI projects are delivered.

**Original RFM page** — Page 3 was not in the guided project. RFM is used by every major bank and fintech to segment customers and predict churn. Computing it in Python and loading it into Power BI as a third analytical layer shows end-to-end thinking.

**Actionable matrix insight** — Wealth customers (highest income) produce only 50 Champions vs Retail's 596. That's a real business problem hiding in the data.

**1,022 inactive accounts identified** — 20.4% of the customer base never completed a transaction. Business can act on this immediately.

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
  <img src="https://img.shields.io/badge/▶️ Dashboard Demo-Check it out-FF0000?style=for-the-badge&logo=youtube&logoColor=white"/>
</a>
