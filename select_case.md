# Binary Tree Nodes
## Overview
*From Hacker Rank*
You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:
- Root: If node is root node.
- Leaf: If node is leaf node.
- Inner: If node is neither root nor leaf node.

## Sample Data
|N|P|
|---|---|
|1|2| 
|3|2|
|6|8|
|9|8|
|2|5|
|8|5|
|5|null|


## Sample Output
```
1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf
```

## Solution
```SQL
SET NOCOUNT ON;

/*
Enter your query here.
Please append a semicolon ";" at the end of the query and enter your query in a single line to avoid error.
*/
select 
    n, 
    case
        when p is null then "Root"
        when n in (select p from BST) then "Inner"
        else "Leaf"
    end as Type
from BST
order by n
go
```
