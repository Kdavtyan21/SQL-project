Question 1: Out of all recorded visits what's the percentage of those visits resulted in a purchase?

SQL Queries: 

SELECT ROUND(CAST(COUNT(transactions)AS DECIMAL ),3)/(SELECT COUNT(*) FROM all_sessions) * 100 AS purchases  FROM all_sessions
WHERE transactions IS NOT NULL

Answer: 

53% of the visitors made a purchase when visiting the site



Question 2: Which visitor made the most visits to the site?

SQL Queries:

SELECT fullvisitorid, COUNT(fullvisitorid), city, country FROM all_sessions
GROUP BY fullvisitorid, city, country
ORDER BY COUNT(fullvisitorid) DESC

Answer:

Visitor from the Unites Stated made the most visits which is 10 (visitorid: "3608475193341679870")



Question 3: 

SQL Queries:

Answer:



Question 4: 

SQL Queries:

Answer:



Question 5: 

SQL Queries:

Answer:
