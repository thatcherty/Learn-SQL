# Pivot Practice
## Description
*From Hacker Rank Occupations*

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output should consist of four columns (Doctor, Professor, Singer, and Actor) in that specific order, with their respective names listed alphabetically under each column.

Note: Print NULL when there are no more names corresponding to an occupation.

The OCCUPATIONS table is described as follows (including sample data):
|Name|Occupations|
|------|-------|
|Jamie| Professor|
|Damian | Doctor|

## Sample Output
```
Jenny    Ashley     Meera  Jane
Samantha Christeen  Priya  Julia
NULL     Ketty      NULL   Maria
```

## Solution

```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/

select [Doctor], [Professor], [Singer], [Actor]
from (
    select 
        row_number() over (partition by occupation order by name) as  rn, 
        name, 
        occupation
    from occupations
) as source
pivot (
    max(name) for occupation in 
    ([Doctor], [Professor], [Singer], [Actor])
) as pivotTable;

go
```
