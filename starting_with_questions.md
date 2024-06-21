Answer the following questions and provide the SQL queries used to find the answer.

    
**Question 1: Which cities and countries have the highest level of transaction revenues on the site?**


SQL Queries:SELECT city, ROUND(SUM(CAST (totaltransactionrevenue AS DECIMAL))/1000000, 2) AS totalTransactionRevenue FROM all_sessions
WHERE city IS NOT NULL AND totaltransactionrevenue IS NOT NULL
GROUP BY city
ORDER BY totaltransactionrevenue DESC

SELECT country, ROUND(SUM(CAST (totaltransactionrevenue AS DECIMAL))/1000000, 2) AS totalTransactionRevenue FROM all_sessions
WHERE totaltransactionrevenue IS NOT NULL
GROUP BY country
ORDER BY totaltransactionrevenue DESC



Answer: The city with the highest level of transaction revenue on the site is San Francisco and for the country it is United States.




**Question 2: What is the average number of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:



Answer:





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







