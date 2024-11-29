
Queries can create an interim or final answer set. When the query (usualy a SELECT, or SELECT/WHERE) creates an interim answer set you can do some post processing such as the group functions to do things like get totals, sub totals etc.

NOTE: When and how does the WHERE clause and the GROUP function work? The WHERE clause works on the first set of your query and is what creates the subset of data that goes into the interim answer set.
The GROUP function happens AFTER the where and operates on the subset of data

GROUP functions:
- SUM - Numeric Only
- AVG - Numeric Only
- COUNT - Any Type
- MIN - Any Type
- MAX - Any Type
- NOTE - These work on the Non-Null values only

Rule to keep in mind when using group functions
**The level of the group function you are doing must match the level of detail in your select statement**

example
Select OrderID, Sum(UnitPrice) as 'Total Price'
where OrderID in (10248, 10249)

This would fail because we are keeping OrderID in the final table and there are multiple oderid's in there... the Sum over all UnitPrice isn't at the same detail. We would either need to drop the OrderID from the select statement (I think) or do a Groupby OrderID

Other notes. SQL has more basic functions so you sometimes have to do some work arounds. For instance you can't get the entry with the largest value, instead you need to sort it and then limit the return to 1 entry.

There is one addition statement and that is the HAVING clause. This acts just like the WHERE clause but occurs AFTER the group / group by functions work... so for instance select customers and country, group by country and count the costomers then use HAVING where the count is greater than 5
