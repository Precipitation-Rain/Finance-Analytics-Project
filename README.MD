# 💰 Finance Analytics Dashboard — Power BI + Python

An end-to-end financial analytics project built for a banking organization — covering transaction performance, customer behaviour, fees, taxes, and regional trends across multiple business segments. Includes a formal Business Requirements document, Python EDA, and a two-page interactive Power BI dashboard.

![PowerBI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Domain](https://img.shields.io/badge/Domain-Banking%20%26%20Finance-darkgreen?style=flat)

---

## 📌 Project Overview

A financial organization needed a centralized analytical solution to monitor KPIs, understand customer segment behaviour, track transaction performance, and identify high-performing regions — replacing manual reporting with an interactive, filterable dashboard.

This project follows a professional BI delivery workflow:

```
Business Requirements → Data Preparation (Python) → Power BI Dashboard → Drill-Down Grid View
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

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| Data Preparation & EDA | Python, Pandas, Jupyter Notebook |
| Dashboard & Visualisation | Power BI Desktop |
| Data Storage | CSV (customers + transactions) |
| Requirements Documentation | Microsoft Word (.docx) |

---

## 📁 Project Structure

```
Finance-Analytics-Project/
│
├── Finance.ipynb                    # Python EDA — data cleaning, profiling, exploration
├── Finance Analytics Dashboard.pbix # Power BI dashboard (2 pages)
├── Business Requirements.docx       # Formal requirements document
├── customers.csv                    # Customer master data
├── finance_transactions.csv         # Transaction records
└── Images/                          # Dashboard screenshots
```

---

## 🗃️ Dataset

**customers.csv** — Customer master records
- Fields: Customer ID, Name, Gender, Age, State, Occupation, Customer Segment (Retail / Premium / SME / Corporate / Wealth)

**finance_transactions.csv** — Transaction records
- Fields: Transaction ID, Customer ID, Date, Transaction Type, Amount, Fees, Tax, Status (Success / Failed / Pending)

**Transaction Types covered:**
Bill Payment · Card Payment · Deposit · Fee Charge · Interest Credit · Investment · Loan EMI · Refund · Transfer · Withdrawal

---

## 🚀 How to Use

### Power BI Dashboard
1. Download `Finance Analytics Dashboard.pbix`
2. Open in **Power BI Desktop** (free download from Microsoft)
3. If data paths break, re-point to `customers.csv` and `finance_transactions.csv` via Transform Data → Source

### Python EDA
```bash
# 1. Clone the repo
git clone https://github.com/Precipitation-Rain/Finance-Analytics-Project.git
cd Finance-Analytics-Project

# 2. Install dependencies
pip install pandas numpy matplotlib seaborn jupyter

# 3. Open the notebook
jupyter notebook Finance.ipynb
```

---

## 💡 What Makes This Project Different

**Business Requirements document** — Most student BI projects jump straight to building. This project started by defining the exact KPIs, chart types, and filter requirements in a formal document, exactly how real BI delivery projects work in banking and financial services.

**Two-dataset join model** — The dashboard requires joining customer demographic data with transaction records — simulating real-world relational data that analysts work with daily at banks and NBFCs.

**10 transaction type breakdown** — Going beyond simple totals to break down performance by transaction category (Loan EMI, Investments, Refunds, etc.) is the level of granularity that financial stakeholders actually need.

---

## 📬 Author

**Rajvardhan Shewale**
- [GitHub](https://github.com/Precipitation-Rain)
- [LinkedIn](https://www.linkedin.com/in/rajvardhanshewale/)
- [Kaggle](https://www.kaggle.com/shambhushewale)
- [Portfolio](https://sites.google.com/view/rajvardhanshewale1771/home)