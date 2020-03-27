
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

# Weather observation station 2-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-2/problem)
Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.

## Solution-
select round(sum(lat_n),2),round(sum(long_w),2) from station;

# Weather observation station 13-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-13/problem)
Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880  and less than 137.2345. Truncate your answer to  4 decimal places.

## Solution-
select round(sum(Lat_N),4) from station where lat_n>38.7880 and lat_n<137.2345;

# Weather observation station 14-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-14/problem)
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to  4 decimal places.

## Solution-
select round(max(lat_n),4) from station where lat_n<137.2345;

# Weather observation station 15-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-15/problem)
Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.

## Solution-
select round(long_w,4) from station where lat_n<137.2345 order by lat_n desc limit 1;

# Weather observation station 16-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-16/problem)
Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7880. Round your answer to 4 decimal places.


## Solution-
select round(min(lat_n),4) from station where lat_n>38.7880;

# Weather observation station 17-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-17/problem)
Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7880 . Round your answer to 4 decimal places.

## Solution-
select round(long_w,4) from station where lat_n>38.7880 order by lat_n limit 1;


# Weather observation station 18-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-18/problem)
Query the Manhattan Distance between points P1 and P2 and round it to a scale of  4 decimal places.

## Solution-
select round((abs(min(lat_n)-max(lat_n))+abs(min(long_w)-max(long_w))),4) from station;


# Weather observation station 19-
## [Query-](https://www.hackerrank.com/challenges/weather-observation-station-19/problem)
Query the Euclidean Distance between points P1 and P2 and round it to a scale of  4 decimal places.

## Solution-
select round(sqrt(power(max(lat_n)-min(lat_n),2)+power(max(long_w)-min(long_w),2)),4) from station;
