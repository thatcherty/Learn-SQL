# Population Census
## Overview
*From Hacker Rank*

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.


## Solution
```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/

select sum(city.population)
from city
inner join country on country.code = city.countrycode
where country.continent = "Asia"

go
```
