**What are your risk areas? Identify and describe them.**

Mainly I had to check if my primary keys have unique values or if they have any NULL value in those collumns. Also I wanted to check if all date values are withing a reasonable timeframe or if that date even exists.

QA Process:

**Here I'm checking if my sku primary key is unique and the second query checks if there are any NULL values.**
```
SELECT sku, COUNT(*)
FROM products
GROUP BY sku
HAVING COUNT(*) > 1
```
```
SELECT sku 
FROM products
WHERE sku IS NULL
```
Both queries returned an empty answer, meaning that this primary key is unique and doesn't have any NULL values

```
SELECT *
FROM all_sessions
WHERE date > CURRENT_DATE OR date < '1980-01-01' OR date IS NULL
```
```
SELECT *
FROM analytics
WHERE date > CURRENT_DATE OR date < '1980-01-01' OR date IS NULL
```
Both queries also returned an empty answer, therefore the dates seem to be in a reasonable timeframe and not past a current date.
