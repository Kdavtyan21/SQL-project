What issues will you address by cleaning the data?

 First I will address the issue with a lot of data that has too many zeros at the end of the integer, for example unit_price in analytics table, however as I created unit_price column as a bigint insted of double precision it looks like as I updated the dataset the value of unit_price rounded itself up to a nearest whole value, will have to look out for it in the future to avoid similar mistakes. TotalTransactionRevenue column in all_sessions has the same problem so instead of permanently updating the column I just divided the value by a 1,000,000 and rounded it to 2 decimals in the queries when I needed to work with the values to not lose my original data.
  
  All not available cities in in the dataset of all_sessions has been set to null to easier parse though the data.
  
  Removed searchkeyword, productrefundamount, itemquantity, itemrevenue from all_sessions as all values in those colums are null. (After reviewing this I've realized this is a very bad practice in real world and will do alternative methods in the future to ease the parsing through data)



Queries:
UPDATE analytics SET unit_price = unit_price/1000000;


UPDATE  all_sessions SET city = NULL WHERE city = 'not available in demo dataset';


ALTER TABLE all_sessions

DROP COLUMN searchkeyword

DROP COLUMN productrefundamount,

DROP COLUMN itemquantity,

DROP COLUMN itemrevenue;


