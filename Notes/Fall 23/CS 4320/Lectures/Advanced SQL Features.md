### Ordering
- `ORDER BY <order-item-list>`
- `<order-item>: <column><direction>`
- `<direction>: ASC or DESC`
- Orders result rows by values in order items
- Prioritize order items that appear earlier in the list
- Applied after grouping (for group-by queries)
- Items must have unique value per group
### Limiting Output Size
- `Limit <Number>`: Only shows first `<Number>` result rows

### Unknown Values
- `NULL`
- Ternary: Three Value Logic
- `<expression> = TRUE` 
- `<expression> = FALSE` 
- `<expression> IS NULL 
- `WHERE` condition evaluates to `NULL` no result row

### Joins with Unknowns
- Standard join keeps only matching row pairs
- Eliminates rows without matching rows in other table
- To keep rows regardless use `OUTER JOIN`
	-  Fills up fields in missing row with `NULL`
- Keep each row in left table `<table1> LEFT OUTER JOIN <table2> ON`
- Keep each row in right table `<table1> RIGHT OUTER JOIN <table2> ON`
- Keep each row in both tables `<table1> FULL OUTER JOIN <table2> ON`
- 
```
Students(Sid, Sname)
Enrollment(Sid, Cid)
Courses(Cid, Cname)

SELECT Sname, Count(*)
FROM Students JOIN Enrollment
	ON (Students.sid = Enrollment.sid)
GROUP BY Sname
```
### Set Operations
- Union result tuples from two queries
- `<query1> UNION <query2>` Eliminates duplicates
- `<query1> UNION ALL <query2>` Keep duplicates
- Intersect results from two queries
- `<query1> INTERSECT <query2>` 
- Set difference between queries
- `<query1> EXCEPT <query2>` 
- Result from `<query1>, <query2>` must be union compatible

### Query Nesting
- Can use queries as part of another query
- Query instead of table in `FROM`
- Query instead of conjunct in `WHERE`
- Query (containing query) vs sub-query (contained query)
- Correlated vs uncorrelated sub queries
- Correlated sub queries reference containing query
```
SELECT Sname FROM Students
	WHERE gpa >= ALL(SELECT gpa FROM Students)
```

### Sub Queries in Conditions
- Check if sub query result is empty
- `EXISTS(<sub-query>): TRUE` if non-empty
- Check is sub query result contains value
- `<value> IN <sub-query>: TRUE` if contained 
- Check if condition holds for all/some sub-query rows
- `<value> >= ALL(<sub-query>): TRUE` if satisfied for all/some
- Correlated sub queries: sub query refers to the outside
- Iterate over rows from outer (containing) query
- Evaluate sub-query for fixed row in outer query
- Decide whether outer row belongs into result
- 