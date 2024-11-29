The #Join function is one of the most resource intensive functions in SQL. It is used to merge data from two tables when they have a common foreign key. the column name for the foriegn key doesn't need to be the same but it needs to be the same datatype

#inner_join join two tables where the foreign keys from both tables match

when you have the same column name in multiple tables you need to tell SQL which table to grab the column from, otherwise it's ambigous. To tell SQL you prefix the column with the table name seperated by a period. example - employee.employeid

when you are referencing the tables you can create an alias for the duration of the querry if you want to save on typing

#inner_join has two types. implicit and explicit. Implicit is where you say select .. from.. where fk1 = fk2. In this case the join is implied. The explicit inner join uses the Join.. on clause
#inner_join #implicit example
Select LastName, Firstname, count(OrderID)
	from employees, orders
	 where employees.employeeid = orders.employeeid
	 Group By LastName, FirstName
	 Order By 3 desc;
#inner_join #explicit example
Select LastName, Firstname, count(OrderID)
	from employees Join orders
	 on employees.employeeid = orders.employesidd
	 Group By LastName, FirstName
	 Order By 3 desc;
For #inner_join  #explicit and #implicit  are the same

It's possible to link up joins if you need to join data from multiple tables.
#join_linked Example:
SELECT LastName, Firstname, sum(unitprice * quantity) as "Total Sales"
	FROM employees E
		JOIN
		 orders O ON E.employeeid = O.employeeid
			 Join
			 orderdetails D ON O.orderid = D.orderid
GROUP By LastName, Firstname
Order by 3 desc, LIMIT 5;

#cartesian_product is an problem that is easy to make. This occurs when the SQL JOIN creates a product of two tables (i.e. all columns and rows from both tables) before subsetting the tables by the columns you need. This is called an #unqualified_join which occues when you don't fully qualify the JOIN operation witha JOIN/WHERE clause that matches all necessary keys for your answer.

#cartesian_product Example:
Select LastName, Firstname, sum(unitprice * quantity) as "Total Sales"
	FROM employees E, Orders O, orderdetails D
	 WHERE E.employeeid = O.employeeid
GROUP BY LastName, Firstname

note: the above statement is joining three tables but there is only One JOIN/WHERE condition

#cartesian_product example fixed
Select LastName, Firstname, sum(unitprice * quantity) as "Total Sales"
	FROM employees E, Orders O, orderdetails D
	 WHERE E.employeeid = O.employeeid
		 and O.orderid = D.orderid
GROUP BY LastName, Firstname

#cartesian_product to fix you need 1 less join condition for the number of tables you are joining. SO if you are joining 3 tables you need 2 join conditions, etc.

#outer_join this is where it will join all the rows where the keys match plus all the rows from one or the other table. So a #left_outer_join will join all rows where the keys match plus all the rows from the left table even if the keys don't match.
#outer_join uses the LEFT OUTER JOIN or the RIGHT OUTER JOIN in postgres
