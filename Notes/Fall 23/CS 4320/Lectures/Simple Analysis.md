### SQL Queries
- Describes a new relation to generate
- `SELECT`: Describes columns of relation to generate
- `FROM`: Describes source relations and how to match
- `WHERE`: Defines conditions result rows must satisfy
- 
```
SELECT <columns>
FROM <table1> JOIN <table2> ON (<join-pred>)
WHERE <where-pred>
```
- `<columns>` is a comma separated list of columns
- `<table1>, <table2>` are database relations
- `<join-pred>` is a condition defining matching tuple pairs
- `<where-pred>` are additional conditions
- Example:
- ```
```
Database Relations:
Students(Sid, Sname)
Enrollment(Sid, Cid)
Courses(Cid, Cname)

SELECT Students.Sname
FROM Students
	JOIN Enrollment ON (Students.sid = Enrollment.sid)
	JOIN Courses ON (Enrollment.cid = Courses.cid)
WHERE Courses.Cname = 'CS4320'

//Simplify

SELECT S.Sname
FROM Students S
	JOIN Enrollment E ON (S.sid = E.sid)
	JOIN Courses C ON (E.cid = C.cid)
WHERE C.Cname = 'CS4320'

//Omit table name is no ambiguity exists

SELECT Sname
FROM Students S
JOIN Enrollment E ON (S.sid = E.sid)
JOIN Courses C ON (E.cid = C.cid)
WHERE Cname = 'CS4320
```

### Diverse Predicates
- Can use inequalities 
- Not equal `<>`
- Check if value in list `IN`
- Regular Expression: `Cname LIKE 'CS_320%`
	- `%` Zero or more arbitrary characters
	- `_` One arbitrary character

### Composite Predicates
- Logical conjunction `AND`
- Logical disjunction `OR`
- Negation `NOT`

### Diverse Select Clauses
- `*` Selects all columns
- `<table>.*` Selects all columns from `<table>`
- Can use arithmetic expressions in select clause `SELECT 3*(<col-1> + <col-2>)`
- Can assign new names for output columns `SELECT Sname as StudentName`

### Join Syntax Alternatives
- Specify names of columns that appear in multiple tables
	- `<table1> JOIN <table2> USING (<column>)`
	- Abbreviates `<table1> JOIN <table2> ON (<table1>.<column> = <table2>.<column>)`
- Natural joins match values in column with same name
	- `<table1> NATURAL JOIN <table2>`
	- Introduces equality conditions between columns of same name
- No join keyword: `FROM <table1><table2> WHERE <join-condition>`

### Distinct Results
- `SELECT` can generate the same row multiple times
- `SELECT DISTINCT` Eliminates duplicates

### Aggregation Queries
- Calculate aggregates over all rows of result relation
- `SUM, AVG, MIN, MAX` Numerical expression parameter
- `COUNT(*)` Counts rows in result relation
- `COUNT(<column>)` Count rows with value in `<column>`
- `COUNT(DISTINCT <column>)` Counts number of distinct values in `<column>` in result relation
- 
```
Database Relations:
Students(Sid, Sname)
Enrollment(Sid, Cid)
Courses(Cid, Cname)

SELECT Count(*)
FROM Students
	JOIN Enrollment ON (Students.sid = Enrollment.sid)
	JOIN Courses ON (Enrollment.cid = Courses.cid)
WHERE Courses.Cname = 'CS4320'
```

### Aggregation By Group
- Common: Want aggregates for multiple data subsets
- `GROUP-BY` to define data subsets
- `GROUP BY <column-list>` Distinguish data subsets based on their values in specified columns
- 
```
Database Relations:
Students(Sid, Sname)
Enrollment(Sid, Cid)
Courses(Cid, Cname)

SELECT Count(*), Cname
FROM Students
	JOIN Enrollment ON (Students.sid = Enrollment.sid)
	JOIN Courses ON (Enrollment.cid = Courses.cid)
WHERE Cname IN ('CS4320', 'CS5320')
GROUP BY Cname
```

### Grouping
- Grouping is allied after pairing data sources `FROM` and filtering rows `WHERE`
- Result contains one row per group
- Implies restriction on `SELECT` clause
- Only expression with unique value per group
- This includes aggregates and grouping columns
- Condition in `WHERE` applies to single rows (evaluated before grouping)
- `HAVING` specifies condition on groups (evaluated after grouping)
- ```
```
Database Relations:
Students(Sid, Sname)
Enrollment(Sid, Cid)
Courses(Cid, Cname)

SELECT Count(*), Cname
FROM Students
	JOIN Enrollment ON (Students.sid = Enrollment.sid)
	JOIN Courses ON (Enrollment.cid = Courses.cid)
WHERE Cname IN ('CS4320', 'CS5320')
GROUP BY Cname
HAVING Count(*) >= 100
```