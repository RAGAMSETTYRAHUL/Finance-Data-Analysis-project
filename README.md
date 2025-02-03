# 📊 Finance Data Analysis Using SQL, Python, and Power BI

## 📌 Overview
This project analyzes **financial transactions** using **SQL for data querying, Python (Pandas) for data cleaning, and Power BI for visualization**. The goal is to extract key financial insights and identify trends based on the dataset.

---

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

---

## 📌 Tools & Technologies Used
- **SQL (MySQL)** – Data extraction and key metric calculations  
- **Python (Pandas)** – Data cleaning and transformation  
- **Power BI (DAX)** – Interactive visualizations and insights  

---

## 📊 Key Analyses & Visualizations
1️⃣ **Total Revenue (KPI Card)** – Overall financial performance  
2️⃣ **Monthly Revenue Trend (Line Chart)** – Revenue trends over time  
3️⃣ **Top Customers by Spending (Bar Chart)** – Identifying high-value customers  
4️⃣ **Revenue by Payment Method (Pie Chart)** – Understanding preferred payment methods  
5️⃣ **Most Popular Category (Column Chart)** – Top-performing product/service categories  

---

## 📝 SQL Queries
### 1️⃣ Total Revenue  
```sql
SELECT SUM(Amount) AS Total_Revenue FROM finance_transactions;

2️⃣ Monthly Revenue

SELECT DATE_FORMAT(Date, '%Y-%m') AS Month, SUM(Amount) AS Monthly_Revenue
FROM finance_transactions
GROUP BY Month
ORDER BY Month ASC;

3️⃣ Top 5 Customers by Spending

SELECT Customer_ID, SUM(Amount) AS Total_Spending
FROM finance_transactions
GROUP BY Customer_ID
ORDER BY Total_Spending DESC
LIMIT 5;

🐍 Data Cleaning with Python (Pandas)

Steps:
1.Remove Duplicates
2.Handle Missing Values
3.Convert Data Types
4.Remove Invalid Transactions
5.Save Cleaned Data

Python Script (data_cleaning.py)

import pandas as pd

# Load dataset
df = pd.read_csv("finance_transactions.csv")

# Drop duplicates
df.drop_duplicates(inplace=True)

# Fill missing values
df["Amount"].fillna(df["Amount"].mean(), inplace=True)
df["Category"].fillna("Unknown", inplace=True)

# Convert 'Date' column to DateTime format
df["Date"] = pd.to_datetime(df["Date"])

# Remove negative or zero transaction amounts
df = df[df["Amount"] > 0]

# Save cleaned data
df.to_csv("cleaned_finance_transactions.csv", index=False)
print("Data cleaning complete. File saved as 'cleaned_finance_transactions.csv'.")


📊 Power BI Dashboard Setup
Step 1: Load the Dataset into Power BI
Open Power BI Desktop.
Click on Home > Get Data > Text/CSV.
Select finance_transactions.csv and click Load.
The dataset will appear in the Fields Pane.


Step 2: Data Cleaning in Power Query
Click on Transform Data (Power Query Editor will open).
Check for:
Missing values in Amount, Customer_ID, Date.
Incorrect data types (e.g., Date should be "Date", Amount should be "Decimal").
Blank values in Category and Payment Method.
Click Close & Apply.

Step 3: Create DAX Measures

1️⃣ Total Revenue (KPI Card)
Total Revenue = SUM(finance_transactions[Amount])


2️⃣ Monthly Revenue Trend (Line Chart)
Monthly Revenue = 
SUMMARIZE(finance_transactions, finance_transactions[Date], "Revenue", SUM(finance_transactions[Amount]))

3️⃣ Top Customers by Spending (Bar Chart)
Top Customers = 
TOPN(5, 
    SUMMARIZE(finance_transactions, finance_transactions[Customer_ID], "Total_Spending", SUM(finance_transactions[Amount])), 
    [Total_Spending], DESC)
4️⃣ Revenue by Payment Method (Pie Chart)
Revenue by Payment = 
SUMMARIZE(finance_transactions, finance_transactions[Payment_Method], "Total_Revenue", SUM(finance_transactions[Amount]))

5️⃣ Most Popular Category (Column Chart)

Most Popular Category = 
SUMMARIZE(finance_transactions, finance_transactions[Category],  "Total_Sales", SUM(finance_transactions[Amount]))

📂 Project Structure

📂 finance-data-analysis
 ├── 📄 finance_transactions.csv   # Raw Dataset
 ├── 📄 cleaned_finance_transactions.csv # Cleaned Dataset
 ├── 📄 analysis.sql               # SQL Queries
 ├── 📄 data_cleaning.py           # Python Script (Pandas Data Cleaning)
 ├── 📄 finance_dashboard.pbix     # Power BI File
 ├── 📄 README.md                  # Project Documentation

📌 Conclusion
This project provides valuable insights into financial transactions using SQL, Python, and Power BI. It helps in tracking revenue trends, identifying top customers, and optimizing financial strategies.

📩 Connect With Me
📧 Email: ragamsettyrahul7@gmail.com
🔗 LinkedIn: RAGAMSETTY RAHUL
