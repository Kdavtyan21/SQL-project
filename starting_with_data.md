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



Question 3: Which way/type did visitors know or visited the site? Eg: Through referral or organic web search.

SQL Queries:

SELECT channelgrouping, COUNT(channelgrouping) AS count FROM all_sessions
GROUP BY channelgrouping
ORDER BY count DESC

Answer:

Majority of visitors visited or searched for the  site through organic search (8653 visitors out of 15134)


Question 4:

During which month and year was teh site the most visited?

SQL Queries:

SELECT (EXTRACT(year FROM date)) as year, COUNT(EXTRACT(year FROM date)) AS visits FROM all_sessions
GROUP BY EXTRACT(year FROM date)

SELECT (EXTRACT(month FROM date)) as month, COUNT(EXTRACT(month FROM date)) AS visits FROM all_sessions
GROUP BY EXTRACT(month FROM date)
ORDER BY visits DESC


Answer:

The most visits by month was in August with 2074 visits and for year, between 2016 and 2017, it was 2017 with 8130 visits


Question 5: How long on average do people spend their time on the site in minutes?

SQL Queries:

SELECT AVG(timeonsite)/60 AS time_spent_on_average, COUNT(timeonsite) FROM all_sessions
WHERE timeonsite IS NOT NULL

SELECT AVG(timeonsite)/60 AS time_spent_on_average, COUNT(timeonsite) FROM all_sessions
WHERE timeonsite IS NOT NULL AND transactions IS NOT NULL

Answer: 

Time spent on average on the site is around 4 minutes but if we only count visitors that made a purchase then it would be 9 minutes


