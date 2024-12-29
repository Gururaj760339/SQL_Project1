**Project Name**: Retail Sales Analysis

**Level:** Beginner

**Database:** raj


This project design to demonstrate SQL skills and techniques typically used by data analysis to explore, clean and analyze retail sales data. the project involves setting up a retail sales database, perfoming exploratory data analysis (EDA) and answering specific business question through SQL quries. this project is ideal for those who are starting their journey in data analysis and want to build a solid foundation in SQL.

*****Objectives*****

**1. Set up a retail sales database:** create and populate a retail sales database with the provided sales data.

**2. Data Cleaning:**  Identify and remove any records with missing or null values.

**3. Exploratory Data Analysis:**  Perform basic exploratory data analysis to understand the dataset.

**4. Business Analysis:** nUse Sql to answer spccific business question and derive insights the sales data.


**Project Structure**

**1. Database Setup**

**Database Creation:** The project starts by creating a database name raj

**Table Creation:** a table named sales is created to store the sales data. the table structure includes columns for transaction id, sale date, sale time, customer id, gender, age, product category, quantity sold, price per unit, cost of goods sold and total sale amount.


CREATE DATABASE raj;


CREATE TABLE sales
(    transactions_id INT PRIMARY KEY,
    
    sale_date DATE,	
    
    sale_time TIME,
    
    customer_id INT,	
    
    gender VARCHAR(10),
    
    age INT,
    
    category VARCHAR(35),
    
    quantity INT,
    
    price_per_unit FLOAT,	
    
    cogs FLOAT,
    
    total_sale FLOAT
    
);


**2. Data Exploration and Cleaning**

**Record count:** Detamine the total number of records in the dataset.

**Customer Count:** Find out how many unique customers are in the dataset.

**Category Count: **identify all unique product categories in the dataset.

**Null Value Check:** Check for any null values in the dataset and records with missing value in the dataset and delete records with missing data.






