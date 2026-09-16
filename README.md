# Opay-Transaction-Performance-and-Insights

##  Executive Summary
OPay processes millions of transactions daily across multiple channels (Web, App, POS, USSD) and customer types (Individual, Merchant). This project analyzes 5,000 transactions to answer: **What's driving the current 69% success rate, and where are the biggest opportunities across channels, transaction types, and locations?**

##  Tools Used
- **Excel / WPS Office** — data cleaning, pivot tables, calculated KPIs
- **Tableau Public** — dashboard design and visualization

##  Process
1. **Data cleaning**: Started with raw transaction data (12 fields: Transaction ID, Date, Customer ID/Type, Location, Transaction Type, Channel, Amount, Status, Fee, Response Time, Merchant Category)
2. **KPI calculation**: Built pivot tables to calculate Total Transactions, Total Fees, Total Transaction Value, Average Transaction Value, and Success Rate
3. **Segmentation**: Broke down performance by transaction status (Failed/Pending/Reversed/Successful), channel (Web/App/POS/USSD), customer type (Individual/Merchant), and location
4. **Dashboard build**: Connected cleaned data to Tableau and designed KPI cards, bar charts, and ranking tables

##  Key Findings
- **Success rate sits at 69.12%** — but failures aren't concentrated in one issue. Failed (503), Pending (542), and Reversed (499) transactions are each roughly 10% of total volume, pointing to three separate friction points rather than one dominant problem.
- **Individual transactions drive ~80% of total value** (₦1.005B) vs Merchant transactions at ~20% (₦246M).
- **Channel usage is evenly distributed** — Web, App, POS, and USSD all fall within a tight ₦20M range (₦299M–₦320M), meaning no single channel dominates.
- **On the Web channel specifically, Bill Payment leads** (₦74.2M) followed by Data purchases (₦68M) — but this shifts locally: in Benin City (the top web location), **Data purchases actually outrank Bill Payment**.
- **Lagos underperforms on Web transactions**, ranking 6th of 8 cities despite being Nigeria's largest — Benin City, Kaduna, and Abuja all rank higher.

##  Recommendation
Investigate the Failed/Pending/Reversed transaction paths individually rather than as one combined issue, since each represents a distinct ~10% leak. Additionally, city-level differences in transaction type behavior (e.g., Benin City vs Lagos) suggest OPay could benefit from localized product promotions rather than a one-size-fits-all national strategy.

## 📊 Dashboard
[Link to your Tableau Public dashboard]
