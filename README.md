# Fetch-Data-Analyst-Assessment

# 📊 Data Analysis & Insights Dashboard  

Welcome to the **Data Analysis & Insights Dashboard**, where we dive deep into user behavior, sales trends, and product performance using Power BI. This repository contains key findings, SQL queries, visualizations, and recommendations based on the provided datasets. 🚀  

---

## 📂 Project Overview  

This project analyzes three datasets:  

1. **USER_TAKEHOME.csv** – User demographic and account information.  
2. **PRODUCTS_TAKEHOME.csv** – Product category and brand details.  
3. **TRANSACTION_TAKEHOME.csv** – Transactional data, including receipts, purchases, and sales.  

We aim to uncover actionable insights to help improve business decisions and optimize performance.  

---

## 📈 Key Findings  

### 🚨 **Data Quality Issues Identified**  
- **Missing Data:** Significant gaps in key fields such as `CATEGORY_3`, `CATEGORY_4`, and `MANUFACTURER`.  
- **Inconsistent Date Formats:** Variations in date representations across datasets (`CREATED_DATE` vs. `PURCHASE_DATE`).  
- **Duplicate Entries:** Some barcode values appear multiple times, raising concerns about data integrity.  

**👉 Suggested Action:** Collaborate with the data engineering team to clean and standardize the datasets.  

---

### 🔍 **Interesting Trends Discovered**  

1. **Power Users Drive Revenue:** Users with accounts older than six months contribute significantly to total sales, making them valuable targets for retention strategies.  
2. **Top-Selling Brands:** Certain brands dominate sales in specific categories, with the potential for cross-selling opportunities.  
3. **Growth Insights:** The company has shown consistent year-over-year (YoY) growth, with seasonal peaks in sales that can be leveraged for targeted campaigns.  

---

## 📊 Power BI Dashboard Highlights  

The Power BI dashboard includes the following **key visualizations** to help stakeholders make data-driven decisions:  

### **1. User Demographics & Behavior 🧑‍🤝‍🧑**  
- **Age Distribution:** Histogram of different user generations.  
- **Gender & Language Insights:** Pie charts to visualize diversity.  


### **2. Sales Performance 💰**  
- **Year-over-Year Growth:** Line charts showcasing revenue trends.  
- **Category Contributions:** Stacked bar charts comparing product categories.  
- **Store-Level Performance:** Geographical insights for better supply chain management.  

### **3. Product Performance 🛍️**  
- **Top Brands:** Horizontal bar charts of highest-performing brands.  
- **Product Sales Heatmap:** Visualizing barcode-level sales.  

---

## 🛠️ SQL Queries Used  

Below are some of the SQL queries used to derive key insights from the data:  

### 1️⃣ **Top 5 Brands by Receipts Scanned Among Users 21 and Over**  
```sql
SELECT P.BRAND, COUNT(T.RECEIPT_ID) AS total_scans 
FROM TRANSACTION_TAKEHOME T 
JOIN PRODUCTS_TAKEHOME P ON T.BARCODE = P.BARCODE 
JOIN USER_TAKEHOME U ON T.USER_ID = U.ID 
WHERE DATEDIFF(YEAR, U.BIRTH_DATE, GETDATE()) >= 21 
GROUP BY P.BRAND 
ORDER BY total_scans DESC 
LIMIT 5;
```

### 2️⃣ **Year-over-Year Growth Rate Calculation**  
```sql
SELECT 
    YEAR(PURCHASE_DATE) AS sales_year,
    SUM(FINAL_SALE) AS total_sales,
    LAG(SUM(FINAL_SALE)) OVER (ORDER BY YEAR(PURCHASE_DATE)) AS previous_year_sales,
    ((SUM(FINAL_SALE) - LAG(SUM(FINAL_SALE)) OVER (ORDER BY YEAR(PURCHASE_DATE))) / 
      LAG(SUM(FINAL_SALE)) OVER (ORDER BY YEAR(PURCHASE_DATE))) * 100 AS YoY_growth
FROM TRANSACTION_TAKEHOME
GROUP BY YEAR(PURCHASE_DATE)
ORDER BY sales_year;
```

---

## 📅 Next Steps & Recommendations  

1. **Data Quality Improvement:** Address missing and inconsistent data points with the data engineering team.  
2. **Advanced User Segmentation:** Use Power BI filters to personalize recommendations based on demographics.  
3. **Retention Strategies:** Focus on high-value users and increase customer lifetime value through engagement campaigns.  
4. **Forecasting:** Leverage AI capabilities in Power BI to predict future sales trends based on historical data.  

---

## 📧 Contact  

For any questions or feedback, reach out to me at:  
📨 Email: [akutre@hawk.iit.edu]()  
💼 LinkedIn: https://linkedin.com/in/yourprofile](https://www.linkedin.com/in/aditya-kutre-906a24131 
