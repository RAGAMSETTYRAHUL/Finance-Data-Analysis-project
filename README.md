# 📊 Finance Data Analysis Using SQL, Python, and Power BI

## 📌 Overview
This project analyzes **financial transactions** using **SQL for data querying, Python (Pandas) for data cleaning, and Power BI for visualization**. The goal is to extract key financial insights and identify trends based on the dataset.

## 📂 Dataset Information
- **File:** `finance_transactions.csv`
- **Records:** 500 transactions
- **Columns:**
  - `Transaction_ID` – Unique ID for each transaction
  - `Date` – Date of transaction
  - `Customer_ID` – Unique identifier for customers
  - `Category` – Transaction category (Groceries, Electronics, etc.)
  - `Amount` – Transaction amount (in USD)
  - `Payment_Method` – Payment type (Credit Card, Debit Card, etc.)
  - `Status` – Transaction status (Completed, Failed, Pending)

## 📌 Tools & Technologies Used
- **SQL (MySQL)** – Data extraction and key metric calculations  
- **Python (Pandas)** – Data cleaning and transformation  
- **Power BI (DAX)** – Interactive visualizations and insights  

## 📊 Key Analyses & Visualizations
1️⃣ **Total Revenue (KPI Card)** – Overall financial performance  
2️⃣ **Monthly Revenue Trend (Line Chart)** – Revenue trends over time  
3️⃣ **Top Customers by Spending (Bar Chart)** – Identifying high-value customers  
4️⃣ **Revenue by Payment Method (Pie Chart)** – Understanding preferred payment methods  
5️⃣ **Most Popular Category (Column Chart)** – Top-performing product/service categories  

## 📝 SQL Queries
Queries used to extract key insights:  

```sql
-- Total Revenue
SELECT SUM(Amount) AS Total_Revenue FROM finance_transactions;

-- Monthly Revenue
SELECT DATE_FORMAT(Date, '%Y-%m') AS Month, SUM(Amount) AS Monthly_Revenue
FROM finance_transactions
GROUP BY Month
ORDER BY Month ASC;

-- Top 5 Customers by Spending
SELECT Customer_ID, SUM(Amount) AS Total_Spending
FROM finance_transactions
GROUP BY Customer_ID
ORDER BY Total_Spending DESC
LIMIT 5;
