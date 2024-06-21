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


SELECT ROUND(AVG(counts)) AS average_purchase FROM(
SELECT country, COUNT(productsku) AS counts
FROM all_sessions
WHERE city IS NOT NULL AND country IS NOT NULL
GROUP BY city, country)
ORDER BY AVG(counts) DESC

SELECT country, ROUND(AVG(counts)) AS average_purchase FROM(
SELECT country, COUNT(productsku) AS counts
FROM all_sessions
WHERE city IS NOT NULL AND country IS NOT NULL
GROUP BY city, country)
GROUP BY country
ORDER BY AVG(counts) DESC

SELECT city, ROUND(AVG(counts))  AS average_purchase FROM(
SELECT city, COUNT(productsku) AS counts
FROM all_sessions
WHERE city IS NOT NULL AND country IS NOT NULL
GROUP BY city, country)
GROUP BY city
ORDER BY AVG(counts) DESC


Answer:
Just the total average between all cities and countries is 21 (First query) the other 2 queries will show you the average number of products bought from every country or city.






**Question 3: Is there any pattern in the types (product categories) of products ordered from visitors in each city and country?**


SQL Queries:

SELECT  v2productcategory, COUNT(v2productcategory) FROM all_sessions
WHERE country IS NOT NULL AND country != '(not set)'
GROUP BY v2productcategory
ORDER BY COUNT(v2productcategory) DESC

SELECT country, v2productcategory, COUNT(v2productcategory) FROM all_sessions
WHERE country IS NOT NULL AND country != '(not set)'
GROUP BY country, v2productcategory
ORDER BY COUNT(v2productcategory) DESC

SELECT city, v2productcategory, COUNT(v2productcategory) FROM all_sessions
WHERE city IS NOT NULL AND city != '(not set)'
GROUP BY city, v2productcategory
ORDER BY COUNT(v2productcategory) DESC

SELECT v2productcategory, COUNT(v2productcategory) FROM all_sessions
WHERE city IS NOT NULL AND city != '(not set)'
GROUP BY v2productcategory
ORDER BY COUNT(v2productcategory) DESC

Answer:

It looks like the majority of product categories of the product, be it countries or cities, is bought from Youtube or Men's-T-Shirt category





**Question 4: What is the top-selling product from each city/country? Can we find any pattern worthy of noting in the products sold?**


SQL Queries:



Answer:





**Question 5: Can we summarize the impact of revenue generated from each city/country?**

SQL Queries:



Answer:







