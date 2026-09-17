# OPay Transaction Performance & Insights

## Executive Summary

An analysis of 5,000 OPay transactions (₦1.25B total value) across four channels and eight Nigerian cities to identify where transaction performance breaks down and where growth opportunities sit.

The headline finding: OPay's 69.12% success rate is not caused by one broken process. Failed, Pending, and Reversed transactions each account for roughly 10% of volume independently — meaning three separate fixes are needed, not one. A second finding is that channel usage is almost perfectly even (all four channels within a ₦20M band), so there is no "primary" channel to prioritise. Most actionable: transaction-type preferences shift by city, with Benin City favouring Data purchases while the national Web trend favours Bill Payment — pointing to localised rather than national strategy.

## Business Problem

OPay operates across Web, App, POS, and USSD channels serving both individual and merchant customers. With nearly a third of transactions failing to complete successfully, the business needs to know:

1. What is actually driving the ~31% non-success rate — is it one dominant failure mode or several?
2. Which channels and customer segments carry the most value, and should resources be concentrated anywhere?
3. Do transaction behaviours differ by location in ways that would justify regional strategy?

## Objective

- Quantify the scale and composition of transaction failures (Failed, Pending, Reversed) to determine whether one fix or several are needed
- Compare performance and value across channels (Web, App, POS, USSD) to identify where investment is justified
- Compare individual vs. merchant customer contribution to total transaction value
- Identify whether transaction-type preferences vary meaningfully by city, to test the case for localised vs. national strategy
- Present findings in an interactive dashboard that business stakeholders can explore without needing to read raw data

## Dataset

**Source:** OPay transaction records — 5,000 rows, 12 fields.

| Field | Description |
|---|---|
| Transaction_ID | Unique transaction identifier |
| Transaction_Date | Date of transaction (2019–2025) |
| Customer_ID | Unique customer identifier |
| Customer_Type | Individual or Merchant |
| Location | City (8 Nigerian cities) |
| Transaction_Type | Airtime, Bill Payment, Data, POS Payment, Transfer |
| Channel | Web, App, POS, USSD |
| Amount | Transaction value (₦) |
| Transaction_Status | Successful, Failed, Pending, Reversed |
| Fee | Fee charged (₦) |
| Response_Time_Sec | Processing time in seconds |
| Merchant_Category | Electronics, Fashion, Food & Restaurants (N/A for individuals) |

**Scale:** ₦1,251,725,247 total transaction value · ₦2,503,125 total fees · ₦250,345 average transaction value

## Tools

- **Excel / WPS Office** — data cleaning, pivot tables, KPI calculation
- **Tableau Public** — dashboard design and visualisation

## Data Cleaning

Before analysis, the raw transaction data was reviewed and prepared in Excel/WPS:

- **Duplicate check:** Verified each `Transaction_ID` was unique
- **Missing value check:** Reviewed all 12 fields for blanks, with `Merchant_Category` expected to be blank for Individual customers (not treated as missing data)
- **Consistency check:** Standardised text fields (e.g., city names, channel names, transaction status labels) to avoid duplicate categories caused by inconsistent casing or spacing
- **Type formatting:** Ensured `Amount`, `Fee`, and `Response_Time_Sec` were stored as numeric fields (not text) so pivot tables and KPI formulas calculated correctly
- **Date formatting:** Standardised `Transaction_Date` to a consistent date format for accurate year/month grouping

## Methodology

1. **Load & Inspect** — Reviewed the raw dataset (5,000 rows, 12 fields) in Excel/WPS
2. **Clean & Standardise** — Applied the checks above to ensure the data was consistent and calculation-ready
3. **Build KPIs & Pivot Tables** — Calculated total value, fee totals, average transaction value, and status/channel breakdowns
4. **Exploratory Analysis** — Broke down transactions by status, channel, customer type, transaction type, and location to surface patterns
5. **Visualize** — Built an interactive Tableau dashboard to present the findings

## Exploratory Data Analysis

**1. Transaction status distribution**

| Status | Count | Share |
|---|---|---|
| Successful | 3,456 | 69.1% |
| Pending | 542 | 10.8% |
| Failed | 503 | 10.1% |
| Reversed | 499 | 10.0% |

The three failure states are near-identical in size — an unusual pattern suggesting three independent causes rather than one systemic fault.

**2. Channel distribution (total value)**

| Channel | Value |
|---|---|
| WEB | ₦319,922,550 |
| App | ₦318,381,213 |
| POS | ₦313,792,978 |
| USSD | ₦299,628,506 |

A spread of only ₦20M across all four — remarkably even usage.

**3. Customer type split**

Individual customers account for ₦1,005,576,335 (~80%) of total value; merchants ₦246,148,912 (~20%). Within each segment, channel preference again shows minimal variation.

**4. Web channel deep-dive**

Transaction types on Web, ranked: Bill Payment (₦74.2M), Data (₦68M), Transfer (₦63.1M), POS Payment (₦60.2M), Airtime (₦54.3M).

**5. Geographic ranking (Web channel)**

Benin City (₦44.1M), Kaduna (₦43.0M), Abuja (₦42.9M), Kano (₦41.4M), Port Harcourt (₦41.1M), Lagos (₦37.1M), Ibadan (₦35.4M), Enugu (₦35.0M).

**6. City-level drill-down**

Within Benin City, the ranking inverts: Data (₦11.2M) leads, ahead of Bill Payment (₦9.7M) and Airtime (₦9.0M) — the national pattern does not hold locally.

## Key Findings

- **The 69.12% success rate masks three separate ~10% problems.** Failed, Pending, and Reversed are each independently sized, so a single root-cause fix would recover at most a third of lost transactions.
- **Individual customers drive ~80% of transaction value** (₦1.005B vs ₦246M), making them the dominant revenue segment despite merchants typically being the higher-value account type.
- **No channel dominates.** All four sit within ₦20M of each other, so channel-level investment decisions cannot be justified on volume alone.
- **Lagos underperforms on Web**, ranking 6th of 8 cities despite being Nigeria's largest urban market — a gap worth investigating.
- **Transaction-type preference is location-dependent.** Benin City's leading Web transaction type (Data) differs from the national leader (Bill Payment).

## Recommendations

1. **Treat the three failure states as separate investigations.** Pending transactions likely indicate timeout or settlement delays; Reversed suggests post-authorisation issues; Failed points to validation or connectivity. Each needs its own diagnostic path.
2. **Investigate the Lagos Web gap.** Underperformance in the largest market suggests either a product-fit issue or an untapped opportunity.
3. **Localise product promotion.** City-level differences in transaction type mean national campaigns will underperform targeted ones.
4. **Protect the individual-customer segment**, which carries four-fifths of transaction value.

## Next Steps

- Pull a larger or more recent dataset (e.g., 2026 transactions) to see whether the three-way failure split and city-level patterns hold over time
- Break down Response_Time_Sec by status to check whether slow processing correlates with Pending/Failed transactions
- Segment the Lagos Web underperformance further by transaction type and customer type to narrow down the cause
- Extend the city-level drill-down (currently done for Benin City) to the other seven cities to confirm how widespread the "local pattern differs from national pattern" finding is

## Files

- `Opay Excel Analysis.xlsx` — source workbook with cleaning, pivot tables, and KPI calculations
- Tableau workbook/dashboard — see live link below

## Dashboard

[View the interactive dashboard on Tableau Public](https://public.tableau.com/app/profile/fechi.iroegbu)
