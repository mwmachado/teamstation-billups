# Teamstation Billups Data Analysis

This repository contains a data engineering analysis using sample merchant and historical transaction data.

## Notebook Report

The main implementation and report are in [`notebooks/billups_case_study.ipynb`](notebooks/billups_case_study.ipynb). Open it in GitHub or JupyterLab to review the markdown explanation, PySpark code, result tables, chart, and final recommendations.

## Running The Notebook

This project uses Docker to provide JupyterLab, Python, Spark, PySpark, and parquet support.

```bash
docker compose up
```

Then open JupyterLab at http://localhost:8888 and run:

```text
notebooks/billups_case_study.ipynb
```

## Source Data

- `source/merchants-subset.csv`: sample merchant attributes.
- `source/part-00000-tid-860771939793626614-979f966a-6d53-4896-9692-f81194d27b99-109986-1-c000.snappy.parquet`: sample historical transactions.

Data dictionary source: [Google Sheet](https://docs.google.com/spreadsheets/d/1k05tl92SY5CvEwa0-nFOQMOjkLgZOL9qTXsDsh0F-_Q/edit?gid=0#gid=0).

## Data Dictionaries

### merchants.csv

| Column | Description |
| --- | --- |
| `merchant_name` | Anonymized merchant names, this should appear in reports generated for merchants as "Merchant" |
| `merchant_id` | Unique merchant identifier |
| `merchant_group_id` | Merchant group (anonymized) |
| `merchant_category_id` | Unique identifier for merchant category (anonymized) |
| `subsector_id` | Merchant category group (anonymized) |
| `numerical_1` | anonymized measure |
| `numerical_2` | anonymized measure |
| `most_recent_sales_range` | Range of revenue (monetary units) in last active month --> A > B > C > D > E |
| `most_recent_purchases_range` | Range of quantity of transactions in last active month --> A > B > C > D > E |
| `avg_sales_lag3` | Monthly average of revenue in last 3 months divided by revenue in last active month |
| `avg_purchases_lag3` | Monthly average of transactions in last 3 months divided by transactions in last active month |
| `active_months_lag3` | Quantity of active months within last 3 months |
| `avg_sales_lag6` | Monthly average of revenue in last 6 months divided by revenue in last active month |
| `avg_purchases_lag6` | Monthly average of transactions in last 6 months divided by transactions in last active month |
| `active_months_lag6` | Quantity of active months within last 6 months |
| `avg_sales_lag12` | Monthly average of revenue in last 12 months divided by revenue in last active month |
| `avg_purchases_lag12` | Monthly average of transactions in last 12 months divided by transactions in last active month |
| `active_months_lag12` | Quantity of active months within last 12 months |
| `city_id` | City identifier (anonymized) |
| `state_id` | State identifier (anonymized) |

### historical_transactions.csv

| Column | Description |
| --- | --- |
| `customer_id` | customer identifier |
| `month_lag` | month lag to reference date |
| `purchase_date` | Purchase date |
| `authorized_flag` | Y' if approved, 'N' if denied |
| `category` | anonymized category |
| `installments` | number of installments of purchase |
| `merchant_category_id` | Merchant category identifier (anonymized) |
| `subsector_id` | Merchant category group identifier (anonymized) |
| `merchant_id` | Merchant identifier (anonymized) |
| `purchase_amount` | Purchase amount |
| `city_id` | City identifier (anonymized) |
| `state_id` | State identifier (anonymized) |
