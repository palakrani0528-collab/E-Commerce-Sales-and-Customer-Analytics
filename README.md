# E-Commerce Sales & Customer Analytics    

An end-to-end data analytics project that transforms raw e-commerce transaction data into actionable business insights — from data cleaning in Python to an interactive Power BI dashboard.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)<img width="700" height="393" alt="image" src="https://github.com/user-attachments/assets/a7981e7c-5e0d-4e9c-ab7a-d37234ea264d" />

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) <img width="419" height="359" alt="image" src="https://github.com/user-attachments/assets/ade40c98-882c-434d-a2a7-78bd518777e8" />

![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)<img width="629" height="305" alt="image" src="https://github.com/user-attachments/assets/03dd7205-60d6-4e0f-8f06-97142ac3c004" />

![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)<img width="598" height="321" alt="image" src="https://github.com/user-attachments/assets/45d5d22e-7fc7-4335-a75a-db618d8641d2" />


---

## 📌 Overview

This project analyzes an online retail transactional dataset to uncover revenue trends, top-performing products, customer purchasing behavior, and customer segmentation — helping answer key business questions like:

- What are our monthly revenue trends and seasonal patterns?
- Which products drive the most sales?
- Which countries generate the most revenue?
- Who are our most valuable customers, and who is at risk of churning?
- Which days of the week see peak sales activity?

## 🗂️ Dataset

- **Source:** [Online Retail Dataset — Kaggle](https://www.kaggle.com/datasets/carrie1/ecommerce-data)
- **Description:** Transactional data from a UK-based online retailer, including invoice numbers, product descriptions, quantities, prices, customer IDs, and countries.
- **Size:** ~540,000 raw transactions (reduced to ~1,73,000+ cleaned rows after preprocessing).

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Google Colab** | Data cleaning, EDA, feature engineering (Python) |
| **Pandas / NumPy** | Data manipulation and cleaning |
| **Matplotlib / Seaborn** | Exploratory visualizations |
| **Power BI Desktop** | Interactive dashboard and business reporting |
| **DAX** | Custom measures for KPIs and time-intelligence calculations |
| **Kaggle API** | Dataset sourcing |

## 🔄 Project Workflow

```
Kaggle Dataset → Google Colab (Clean, EDA, Feature Engineering) → Export CSV → Power BI Dashboard
```

### 1. Data Cleaning (Google Colab)
- Removed cancelled orders, negative quantities, and missing Customer IDs
- Removed duplicate records
- Converted data types (dates, IDs)
- Created a `Revenue` column (`Quantity × UnitPrice`)

### 2. Feature Engineering
- Extracted date-based features: `Year`, `Month`, `Day`, `Weekday`, `Hour`
- Built an **RFM (Recency, Frequency, Monetary)** model to segment customers into:
  - **Champions** — most recent, frequent, high-spending customers
  - **Loyal/Recent** — consistently active customers
  - **At Risk/Lost** — customers who haven't purchased recently
  - **Others** — remaining customer base

### 3. Exploratory Data Analysis
- Monthly revenue trends
- Top 10 best-selling products
- Revenue by country
- Sales distribution by day of week
- Customer segment distribution

### 4. Power BI Dashboard
- KPI cards: Total Revenue, Total Orders, Total Customers, Average Order Value
- Revenue trend line chart (monthly)
- Interactive world map showing revenue by country
- Top-selling products (bar chart)
- Sales by weekday (correctly ordered Monday–Sunday using a custom DAX sort column)
- Customer segmentation (RFM-based pie chart)
- Slicers for Date, Country, Segment, and Product filtering

## 📊 Key DAX Measures

```DAX
Total Revenue = SUM(ecommerce_cleaned[Revenue])

Total Orders = DISTINCTCOUNT(ecommerce_cleaned[InvoiceNo])

Average Order Value = DIVIDE([Total Revenue], [Total Orders])

Revenue MoM % = 
VAR CurrentRev = [Total Revenue]
VAR PrevRev = CALCULATE([Total Revenue], DATEADD(ecommerce_cleaned[InvoiceDate], -1, MONTH))
RETURN DIVIDE(CurrentRev - PrevRev, PrevRev)
```

## 📈 Key Insights

-Total revenue reached ₹4.06M across 9K orders from ~3K unique customers, with an average order value of ₹452.57 — indicating a high-frequency, low-to-mid ticket-size retail pattern typical of B2B wholesale.

-Revenue is highly seasonal, peaking around ₹0.68M mid-year before a sharp anomaly drop to ~₹0.08M, then recovering strongly to ₹0.57M by December — suggesting either a data gap for that period or a genuine seasonal dip worth flagging for business review.

-Customer segmentation (RFM analysis) reveals "At Risk/Lost" customers make up the largest segment (~44.7%) of the customer base — a significant churn risk that outweighs "Champions" (~24.6%) and "Loyal/Recent" (~30.7%) segments combined, highlighting an urgent need for customer retention strategies.

-Sales are concentrated in a small set of top products — items like "Medium Ceramic Top Storage Jar" and "Jumbo Bag Red Retrospot" significantly outsell the rest of the catalog, suggesting inventory and marketing focus could be optimized around these bestsellers.

-The United Kingdom dominates revenue contribution, consistent with the dataset's origin as a UK-based online retailer, with other European markets contributing comparatively smaller shares.

-Weekday sales show no activity on Saturdays, indicating the business operates on a Monday–Friday (+Sunday) wholesale cycle rather than typical B2C weekend-driven retail patterns.

## 📁 Repository Structure

```
├── E-Commerce_Data_Analytics_Project.ipynb   # Colab notebook: cleaning, EDA, RFM analysis
├── ecommerce_cleaned.csv                      # Cleaned transactional dataset
├── customer_rfm.csv                           # Customer-level RFM segmentation data
├── E_commerce_dashboard.pbix                  # Power BI dashboard file
├── screenshots/                                # Dashboard preview images
└── README.md
```

## 🚀 How to Run This Project

1. **Clone this repository**
   ```bash
   git clone https://github.com/<your-username>/ecommerce-data-analytics.git
   ```
2. **Run the notebook**
   - Open `E-Commerce_Data_Analytics_Project.ipynb` in Google Colab.
   - Run all cells to reproduce the cleaning, EDA, and RFM analysis.
3. **Open the dashboard**
   - Open `E_commerce_dashboard.pbix` in Power BI Desktop.
   - Click **Refresh** if you've regenerated the CSVs.

## 📷 Dashboard Preview

<img width="700" height="393" alt="Screenshot 2026-07-04 005238" src="https://github.com/user-attachments/assets/8623774a-a3a9-4246-8190-bc6236b83a37" />


```markdown

```

## 🔮 Future Enhancements

- Cohort analysis to track customer retention over time
- Market basket analysis (Apriori algorithm) to identify frequently co-purchased products
- Revenue forecasting using Prophet/statsmodels
- Publish the dashboard to Power BI Service with scheduled refresh

## 👤 Author

**[PALAK RANI]**

---

*This project was built as part of a personal data analytics portfolio to demonstrate skills in data cleaning, exploratory analysis, customer segmentation, and business intelligence dashboarding.*
