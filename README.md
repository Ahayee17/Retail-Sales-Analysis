# Retail-Sales-Analysis SQL Project

## 📝 Project Overview
This project demonstrates SQL skills and techniques typically used by data analysts to explore, clean, and analyze retail sales data. The project involves setting up a retail sales database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries.

## 🎯 Objectives
1- Set up a retail sales database: Create and populate a retail sales table with the provided data.   
2- Data Cleaning: Identify and remove any records with missing or null values.   
3- Exploratory Data Analysis: Perform basic exploratory data analysis to understand the dataset.   
4- Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.   

## 🗂️ Dataset
The dataset used in this project contains retail sales information including:   
1- Transaction ID, Date, Time   
2- Customer details (ID, Gender, Age)   
3- Product category, Quantity sold   
4- Pricing information (Price per unit, COGS, Total sale amount)   

## 🛠️ Project Structure
### 1. Database Setup
**Table Creation:** A table named retail_sales is created to store the sales data.   
**Data Import:** The dataset is imported into the table from a CSV file.   

### 2. Data Cleaning
**Null Value Check:** Queries are executed to identify and remove records with missing data.

### 3. Data Exploration
**Total Sales Count:** Determine the total number of sales records.
**Unique Customer Count:** Identify the number of unique customers.
**Category Distribution:** List all unique product categories.

### 4. Business Analysis
The following business questions were answered using SQL queries:

1- **Sales on Specific Date:** Retrieve all columns for sales made on '2022-11-05'.   
2- **High-Volume Clothing Sales:** Find clothing transactions with quantity > 3 in November 2022.   
3- **Total Sales by Category:** Calculate total sales for each category.   
4- **Average Customer Age in Beauty Category:** Find average age of customers purchasing from the 'Beauty' category.   
5- **High-Value Transactions:** Retrieve all transactions where total_sale > 1000.   
6- **Transactions by Gender and Category:** Count transactions by each gender in each category.   
7- **Monthly Sales Analysis:** Calculate average sales per month and identify the best-selling month in each year.   
8- **Top 5 Customers:** Find the top 5 customers based on highest total sales.   
9- **Unique Customers per Category:** Count unique customers who purchased from each category.   
10- **Shift Analysis:** Create shift classifications (Morning, Afternoon, Evening) and count orders in each shift.   

## 💻 SQL Queries
Here are some of the key SQL queries used in this project:   

```sql
-- Data Cleaning: Remove null values
DELETE FROM retail_sales
WHERE 
    transactions_id IS NULL
    OR sale_date IS NULL
    OR sale_time IS NULL
    OR customer_id IS NULL
    OR gender IS NULL
    OR age IS NULL
    OR category IS NULL
    OR quantiy IS NULL
    OR price_per_unit IS NULL
    OR cogs IS NULL
    OR total_sale IS NULL;

-- Q.3: Total sales by category
SELECT 
    category,
    SUM(total_sale) AS category_total_sales
FROM retail_sales
GROUP BY category;

-- Q.7: Best selling month by year
SELECT 
    year, month, avg_sale
FROM (
    SELECT
        EXTRACT(YEAR FROM sale_date) as year,
        EXTRACT(MONTH FROM sale_date) as month,
        AVG(total_sale) as avg_sale,
        RANK() OVER(PARTITION BY EXTRACT(YEAR FROM sale_date) ORDER BY AVG(total_sale) DESC) AS ranks
    FROM retail_sales
    GROUP BY year, month
)
WHERE ranks = 1;
```

## 📈 Key Findings
**Customer Demographics:** Analysis reveals the age distribution and gender-based purchasing patterns across different product categories.   
**High-Value Transactions:** Identification of transactions exceeding 1000 in total sale value.   
**Sales Trends:** Monthly sales analysis helps identify peak seasons and best-selling months.   
**Product Performance:** Category-wise sales analysis shows which product categories perform best.   
**Customer Insights:** Top customers and unique customer counts per category provide valuable business intelligence.   

## 🤝 Contributing
Feel free to fork this project and submit pull requests for any improvements or additional analyses.   

## 📧 Contact
For any questions or feedback, please reach out:   
Name: [Abdul Hayee]   
Email: [engr.hayee@gmail.com]   
LinkedIn: [https://www.linkedin.com/in/abdul-hayee-1b7a1a2b/]   
GitHub: [https://github.com/Ahayee17]   
