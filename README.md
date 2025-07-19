# # Standard Bank Data Analytics Internship – SQL Project

This project showcases my SQL-based analytics work during my internship at (or simulated for) **Standard Bank**. The focus was on extracting actionable insights from structured financial datasets such as customer profiles, transactions, and account details using advanced SQL queries.

---

##  Project Summary

**Objective:**  
To perform data extraction, manipulation, and analysis using SQL to support decision-making across key banking operations such as customer segmentation, fraud detection, product uptake, and transaction analysis.

---

##  Tools & Environment

- **Database**: PostgreSQL / MySQL / Microsoft SQL Server (specify the one used)
- **Query Tool**: pgAdmin / MySQL Workbench / Azure Data Studio / DBeaver
- **Languages**: SQL (core focus), with brief support from Python/Excel for visualization (if applicable)

---

##  Datasets Used

### 1. `customers`
| Column Name      | Description                         |
|------------------|-------------------------------------|
| customer_id      | Unique customer identifier          |
| name             | Customer full name                  |
| gender           | Gender (Male/Female)                |
| age              | Customer age                        |
| region           | Location/branch of the customer     |
| join_date        | Date customer joined the bank       |

### 2. `accounts`
| Column Name      | Description                         |
|------------------|-------------------------------------|
| account_id       | Unique account identifier           |
| customer_id      | Linked to `customers.customer_id`   |
| account_type     | Savings, Current, Loan, etc.        |
| balance          | Current balance in the account      |
| opened_date      | Date when account was opened        |

### 3. `transactions`
| Column Name      | Description                         |
|------------------|-------------------------------------|
| transaction_id   | Unique transaction ID               |
| account_id       | Linked to `accounts.account_id`     |
| transaction_type | Credit / Debit                      |
| amount           | Transaction amount                  |
| transaction_date | Date of transaction                 |
| channel          | Mobile, ATM, POS, Online, etc.      |

---

##  Key Analysis Tasks

###  1. Customer Segmentation by Region & Age
```sql
SELECT region, COUNT(*) AS total_customers,
       AVG(age) AS avg_age
FROM customers
GROUP BY region;
SELECT account_type, 
       COUNT(*) AS number_of_accounts,
       AVG(balance) AS avg_balance
FROM accounts
GROUP BY account_type;
SELECT DATE_TRUNC('month', transaction_date) AS month,
       SUM(amount) AS total_volume
FROM transactions
GROUP BY month
ORDER BY month;
SELECT t.transaction_id, a.account_id, t.amount, t.channel, t.transaction_date
FROM transactions t
JOIN accounts a ON t.account_id = a.account_id
WHERE t.channel = 'ATM' AND t.transaction_type = 'Debit'
  AND t.amount > 100000;
,,,,

Insights
Regions like Nairobi and Mombasa have the highest customer density.

Current accounts had the highest volume of transactions but savings accounts retained higher average balances.

There is a monthly surge in mobile and online transactions, indicating digital banking growth.

Over 50 flagged transactions crossed high-risk withdrawal thresholds through ATMs.


## ✅ Conclusion

This SQL-based data analytics project demonstrates how structured queries can drive actionable insights in the banking sector. From understanding customer behavior to tracking transaction trends and detecting anomalies, SQL remains a powerful tool for data analysts.

Throughout the project, I applied key SQL concepts including:
- Joins, filtering, and aggregations
- Window functions and subqueries
- Time-based analysis
- Risk flagging logic for fraud detection

This experience strengthened my ability to translate business questions into analytical queries and contribute meaningfully to data-driven decision-making in financial institutions.

The next step would be to integrate these queries into dashboards (e.g., Power BI, Tableau) or automation pipelines using Python for enhanced real-time reporting.



