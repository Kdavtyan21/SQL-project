What issues will you address by cleaning the data?
  First I will address the issue with a lot of data that has too many zeros at the end of the integer, for example unit_price in analytics table, however as I created unit_price column as a bigint insted of double precision it looks like as I updated the dataset the value of unit_price rounded itself up to a nearest whole value, will have to look out for it in the future to avoid similar mistakes 
  All not available cities in in the dataset of all_sessions has been set to null to easier parse though the data



Queries:
UPDATE analytics SET unit_price = unit_price/1000000;

UPDATE  all_sessions SET city = NULL WHERE city = 'not available in demo dataset';
