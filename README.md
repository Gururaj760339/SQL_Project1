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


SELECT * FROM sales
LIMIT 10;

SELECT COUNT(*) FROM sales;


SELECT * FROM sales
WHERE transactions_id ISNULL
	OR sale_date ISNULL
 
	OR sale_time ISNULL
 
	OR customer_id ISNULL
 
	OR gender ISNULL
 
	OR age ISNULL
 
	OR category ISNULL
 
	OR quantiy ISNULL
 
	OR price_per_unit ISNULL
 
	OR cogs ISNULL
 
	OR total_sale ISNULL;
 

DELETE FROM sales

WHERE transactions_id ISNULL

	OR sale_date ISNULL
 
	OR sale_time ISNULL
 
	OR customer_id ISNULL
 
	OR gender ISNULL
 
	OR age ISNULL
 
	OR category ISNULL
 
	OR quantiy ISNULL
 
	OR price_per_unit ISNULL
 
	OR cogs ISNULL
 
	OR total_sale ISNULL;

**3. Data Analysis & Findings**
the following SQL quries were develope to answer Spcific business question:

**Q.1 How many Sales we have?**

SELECT COUNT(*) FROM sales;

**Q.2 How many unique customers we have?**

SELECT COUNT(DISTINCT customer_id) FROM sales;


**Q.3 How many unique category we have?**

SELECT DISTINCT gender FROM sales;


**Q.4 Write a SQL query to retrieve all columns for sales made on '2022-11-05.**
SELECT * FROM sales

WHERE sale_date = '2022-11-05';



**Q.5 Write a SQL query to calculate the total sales (total_sale) for each category.**

SELECT category, SUM(total_sale) AS total_sales FROM sales

GROUP BY category;


**Q-3 Write a SQL query to retrieve all transactions where the category is 'Clothing' and the quantity sold is more than 4 in the month of Nov-2022.**

SELECT * FROM sales

WHERE category = 'Clothing'

	AND
 
		quantiy >=4
  
	AND
 
		TO_CHAR(sale_date, 'YYYY-MM') = '2022-11';
  

**Q-4 Write a SQL query to find the average age of customers who purchased items from the 'Beauty' category.**

SELECT AVG(age) FROM sales

WHERE category = 'Beauty';



**Q-5 Write a SQL query to find all transactions where the total_sale is greater than 1000.**

SELECT * FROM sales

WHERE total_sale> 1000;



**Q-6 Write a SQL query to find the total number of transactions (transaction_id) made by each gender in each category.**

SELECT gender, category, COUNT(*) AS total FROM sales

GROUP BY category, gender;


**Q-7 Write a SQL query to calculate the average sale for each month. Find out best selling month in each year.**


SELECT 

		EXTRACT(MONTH FROM sale_date) AS months,
  
		AVG(total_sale) AS avgsale FROM sales
  
			GROUP BY months
   
			ORDER BY avgsale DESC;
   

**Q-8 Write a SQL query to find the top 5 customers based on the highest total sales.**


SELECT customer_id, SUM(total_sale) AS total_sales FROM sales

GROUP BY 1

ORDER BY total_sales DESC

LIMIT 5;


**Q-9 Write a SQL query to find the number of unique customers who purchased items from each category**.

SELECT category, COUNT(DISTINCT customer_id) AS unique_customers FROM sales

GROUP BY category;


**Q-10 Write a SQL query to create each shift and number of orders (Example Morning <12, Afternoon Between 12 & 17, Evening >17):**


SELECT EXTRACT(HOUR FROM sale_time) AS hours, 

	CASE 
 
		WHEN EXTRACT(HOUR FROM sale_time) > 12 THEN 'Morning' 
  
		WHEN EXTRACT(HOUR FROM sale_time) >= 12 AND EXTRACT(HOUR FROM sale_time) <= 17 THEN 'Afternoon' 
  
ELSE 'Evening' END AS time_of_day 

FROM sales;




