
# The Blunder

## [Query 1-](https://www.hackerrank.com/challenges/the-blunder/problem?h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen&h_r=next-challenge&h_v=zen)

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeroes removed), and the actual average salary.

## Solution-
select ceil(avg(salary)-avg(replace(salary,0,''))) from Employees;

# Top Earners
## [Query2-](https://www.hackerrank.com/challenges/earnings-of-employees/problem?h_r=next-challenge&h_v=zen)

We define an employee's total earnings to be their monthly(salary*months) worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

## Solution-
select months\*salary,count(\*) from employee group by months*salary order by months\*salary desc limit 1;
