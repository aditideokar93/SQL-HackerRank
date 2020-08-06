### Provide a table that provides the region for each sales_rep along with their associated accounts. This time only for the Midwest region. Your final table should include three columns: the region name, the sales rep name, and the account name. Sort the accounts alphabetically (A-Z) according to account name.

SELECT r.name as Reg_nam, s.name as Sales_rep_name, a.name as Acc_name
FROM sales_reps s
JOIN region r
ON r.id=s.region_id AND r.name='Midwest'
JOIN accounts a
ON s.id=a.sales_rep_id
ORDER BY Acc_name;

### Provide a table that provides the region for each sales_rep along with their associated accounts. This time only for accounts where the sales rep has a first name starting with S and in the Midwest region. Your final table should include three columns: the region name, the sales rep name, and the account name. Sort the accounts alphabetically (A-Z) according to account name.

SELECT r.name as Reg_name, s.name as Sales_rep_name,a.name as Acc_name
FROM sales_reps s
JOIN region r
ON (r.id=s.region_id) AND (s.name LIKE 'S%') AND (r.name='Midwest')
JOIN accounts a
ON s.id=a.sales_rep_id
ORDER BY Acc_name;

### Provide a table that provides the region for each sales_rep along with their associated accounts. This time only for accounts where the sales rep has a last name starting with K and in the Midwest region. Your final table should include three columns: the region name, the sales rep name, and the account name. Sort the accounts alphabetically (A-Z) according to account name.

SELECT r.name as Reg_name, s.name as Sales_rep_name,a.name as Acc_name
FROM sales_reps s
JOIN region r
ON (r.id=s.region_id) AND (s.name LIKE '% K%') AND (r.name='Midwest')
JOIN accounts a
ON s.id=a.sales_rep_id
ORDER BY Acc_name;


### Provide the name for each region for every order, as well as the account name and the unit price they paid (total_amt_usd/total) for the order. However, you should only provide the results if the standard order quantity exceeds 100. Your final table should have 3 columns: region name, account name, and unit price.

SELECT r.name as reg_name, a.name as acc_name, (o.total_amt_usd/(o.total+0.01)) as unit_price
FROM accounts a
JOIN orders o
ON o.account_id=a.id AND o.standard_qty>100
JOIN sales_reps s
ON s.id=a.sales_rep_id
JOIN region r
ON s.region_id=r.id;


### Provide the name for each region for every order, as well as the account name and the unit price they paid (total_amt_usd/total) for the order. However, you should only provide the results if the standard order quantity exceeds 100 and the poster order quantity exceeds 50. Your final table should have 3 columns: region name, account name, and unit price. Sort for the smallest unit price first.

SELECT r.name as reg_name, a.name as acc_name, (o.total_amt_usd/(o.total+0.01)) as unit_price
FROM accounts a
JOIN orders o
ON (o.account_id=a.id) AND (o.standard_qty>100) AND (o.poster_qty>50)
JOIN sales_reps s
ON s.id=a.sales_rep_id
JOIN region r
ON s.region_id=r.id
ORDER BY unit_price;


### Provide the name for each region for every order, as well as the account name and the unit price they paid (total_amt_usd/total) for the order. However, you should only provide the results if the standard order quantity exceeds 100 and the poster order quantity exceeds 50. Your final table should have 3 columns: region name, account name, and unit price. Sort for the largest unit price first.

SELECT r.name as reg_name, a.name as acc_name, (o.total_amt_usd/(o.total+0.01)) as unit_price
FROM accounts a
JOIN orders o
ON (o.account_id=a.id) AND (o.standard_qty>100) AND (o.poster_qty>50)
JOIN sales_reps s
ON s.id=a.sales_rep_id
JOIN region r
ON s.region_id=r.id
ORDER BY unit_price desc;


### What are the different channels used by account id 1001? Your final table should have only 2 columns: account name and the different channels. You can try SELECT DISTINCT to narrow down the results to only the unique values.

SELECT DISTINCT w.channel, a.name
FROM accounts a
JOIN web_events w
ON a.id=w.account_id AND a.id=1001;


### Find all the orders that occurred in 2015. Your final table should have 4 columns: occurred_at, account name, order total, and order total_amt_usd.

SELECT o.occurred_at, a.name, o.total, o. total_amt_usd
FROM orders o
JOIN accounts a
ON a.id=o.account_id AND o.occurred_at BETWEEN '01-01-2015' AND '01-01-2016'
ORDER BY o.occurred_at DESC;

