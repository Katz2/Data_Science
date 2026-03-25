//EDA

//Understand the data collected

SELECT  * FROM brightlearn


//Time from 06:00:00 am to 20:59:32 pm
SELECT MIN(transaction_time) AS opening_time, MAX(transaction_time) AS closing_time
FROM brightlearn;

//Month Timeline check
SELECT MONTHNAME(MIN(transaction_date)) AS first_month_transaction, MONTHNAME(MAX(transaction_date)) AS last_month_transaction
FROM brightlearn;

//Check data ranges dates are for the year 2023 from 1st January till 30 June 2023
//Helps figure out when the data end is.
SELECT transaction_date,
DAYNAME(transaction_date),
MONTHNAME(transaction_date)
FROM brightlearn;





//Check above based on quantity 
SELECT transaction_date,
DAYNAME(transaction_date),
MONTHNAME(transaction_date),
transaction_qty
FROM brightlearn;



//Check the peak trading periods.
SELECT transaction_date,
DAYNAME(transaction_date),
MONTHNAME(transaction_date),
EXTRACT(HOUR FROM transaction_time) AS hour,
transaction_qty,
CASE 
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 6 AND 11 THEN 'Morning'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 18 AND 21 THEN 'Evening'
 END AS Period_in_day
FROM brightlearn;




// Most period  sold items in a month
SELECT transaction_date,
MONTHNAME(transaction_date),
EXTRACT(HOUR FROM transaction_time) AS hour,
transaction_qty,
CASE 
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 6 AND 11 THEN 'Morning'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 18 AND 21 THEN 'Evening'
 END AS Period_in_day
FROM brightlearn
ORDER BY transaction_qty DESC
LIMIT 3;



//The most sold products in a day 
SELECT transaction_date,
DAYNAME(transaction_date),
EXTRACT(HOUR FROM transaction_time) AS hour,
SUM()
transaction_qty,
CASE 
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 6 AND 11 THEN 'Morning'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 18 AND 21 THEN 'Evening'
 END AS Period_in_day
FROM brightlearn
ORDER BY transaction_qty DESC;



// Revenue and number of sales in a 6 months period sale. 
SELECT transaction_date,
MONTHNAME(transaction_date)AS month_name,
DAYNAME(transaction_date) AS day_name,
COUNT(DISTINCT transaction_id) AS number_of_sales,
SUM(unit_price*transaction_qty) AS Revenue

FROM brightlearn
GROUP BY transaction_date
ORDER BY transaction_date ASC;


//Best Revenue per store in a Month
SELECT transaction_date,
MONTHNAME(transaction_date) AS month_name,
EXTRACT(HOUR FROM transaction_time) AS hour_,
COUNT(DISTINCT transaction_id) AS number_of_sales,
SUM(unit_price*transaction_qty) AS Revenue,
CASE 
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 6 AND 11 THEN 'Morning'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 12 AND 17 THEN 'Afternoon'
 WHEN EXTRACT(HOUR FROM transaction_time) BETWEEN 18 AND 21 THEN 'Evening'
 END AS Period_in_day
FROM brightlearn
GROUP BY transaction_date, 
    month_name, 

    hour_, 
    Period_in_day
ORDER BY Revenue DESC;


