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

# African Cities
## Overview
*From Hacker Rank*

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

## Solution
```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/

select city.name
from city
inner join country on country.code = city.countrycode
where country.continent = "Africa"

go
```

# Average Pop of each continent
## Overview
*From Hacker Rank*

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

## Solution
```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/

select country.continent, avg(city.population)
from city
inner join country on country.code = city.countrycode
group by country.continent

go
```

# The Report
## Overview
*From Hacker Rank*

You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

## Solution
```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/

select 
    case 
        when g.grade < 8 then null
        else s.name
    end as s_name,
    g.grade,
    s.marks

from students as s
inner join grades as g on s.marks between g.min_mark and g.max_mark

order by g.grade desc, s.name asc, s.marks asc
go
```
