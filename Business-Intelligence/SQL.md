# SQL

## Links
- https://blog.jooq.org/2015/11/07/how-to-find-the-longest-consecutive-series-of-events-in-sql/

## SQL style guide 
- Use consistent descriptive identifiers and names and keep the consice 
- Use underscores in names where you’d naturally use a whitespace 
- Make use of whitespace and indentation to make code easier to read. Indentation should be 4 spaces
- Keep code simple and succint by avoiding anything that is redundant 
- Include comments where necessary using – or /* */
- Avoid abbreviations and if have to use them, make sure they are commonly understood
- Never give a table name the same name as one it’s columns 
- Avoid using a simple ID as a primary identifier for a table. Be more specific 
- Always use lowercase for your naming 
- Aliases should relate to the object they are aliasing – rule of thumb: these should be the first letter of each word in the object’s name (so if there also is an underscore there will be two letters). If there are duplicates, use e.g. s1 and s2 instead. With aliases, always include the AS keyword. Always alias when using multiple tables. When table names are short (ideally they are), consider just adding the entire table name as alias 
- Always use uppercase for SQL specific keywords
- With SQL keywords, use the full lenght keywords (AVERAGE instead of AVG)
- Always include spaces surrounding an = sign, a comma etc. 
- Start on a new line when you’re using AND or OR 
- Group by a number not the column name
- Use 'as' for aliasing tables or fields
- If joining two or more tables, always prefix your column names with the table alias. If only selecting from one table, prefixes are not needed.
- Be explicit about your join (i.e. write inner join instead of join). 
- Distinct should be included on the same row as select. 
- Always rename columns when selecting with table aliases: projects.name as project_name,
- Long Window functions should be split across multiple lines: one for the PARTITION, ORDER and frame clauses, aligned to the PARTITION keyword. Partition keys should be one-per-line, aligned to the first, with aligned commas. Order (ASC, DESC) should always be explicit. All window functions should be aliased.

select 
    X,
    Y, 
    SUM(1) OVER  (PARTITION BY category_id,
                          year
                  ORDER BY pledged DESC
                  ROWS UNBOUNDED PRECEDING) AS category_year
from table_a as a 
left join table_b as b on a.id = b.id 
  and a.date = b.date 
where x.type = 'sql'
  and b.type 'python'


## SQL best practices
- Use CTEs
- Provide meaningful names to each CTE 
- Code for scale, not for one-offs
- Always use the same styling with proper indenting 
- Whenever possible, use window functions
- Use table aliases
- Run the execution or query plan to get an understanding of how the query will perform
- Make sure to comment your code 
- Avoid subqueries as much as possible. 
- Don’t use SELECT *
- In a fact table, use SELECT count(1) instead of count(*). Only use this when you trust the granularity of the fact table
- Write clear code. Explicit over implicit

## SQL order of operations
- In the WHERE clauses, there can be multiple clauses. The top priority will always go to what is between parenthesis. The order of operations follows that of arithmetic, so AND gets priority over OR (but still only after evaluating the parenthesis)
- Order of operations of a query (note the query plan might deviate from this, but this is what happens logically, not necessarily actually):
    - FROM: first we get all the rows from the tables (including any joins)
    - WHERE – filter the rows. Used to limit rows returned from query. Only rows meeting the WHERE clause are being returned. 
    - GROUP BY: take the rows remaining after WHERE and put them in groups 
    - Aggregations: now that you have a group, you can do aggregations for these groups. You can’t put an aggregation in WHERE: it’s value cannot be accessed yet. Aggregate functions can only access groups – therefore everything needs to be grouped 
    - HAVING: now we can use aggregate functions. Because having is after group by, we can no longer access columns or expressions that were not GROUP BY columns 
    - Window functions. Because this is after the aggregate functions, we can nest aggregate functions in window functions. 
    - SELECT Now we can use the rows produced from the clauses above and use create new rows using SELECT. 
    - DISTINCT: we first need to know all rows and columns before we can only retrieve distinct rows
    - UNION, INTERSECT, EXCEPT. This will always happen later, as it depends on everything being run prior
    - ORDER BY: postpone the ordering till only after you know everything that needs to be retrieved
    - LIMIT FETCH TOP: this is happening at the very end  
- Query plan: set of steps executed by the database management system to complete the query. It shows an execution plan with the exact logic flow to use. Each of these costs has a costs (when something is hard to do; we say it’s expensive). Query plans should be read from right to left. When a query is slow, think of another way to write it and compare the execution plans. The DBMS parses the SQL to create a query plan that is based on the lowest costs. 

## Window functions
### General
- A window function performs a calculation across a set of table rows that are somehow related to the current row
- The OVER() clause specifies the window, where the PARTITION defines the current group of rows considered for the window. The ORDER defines the order (within the partition). Without an ORDER BY, the logic is to not do any incremental steps but just do the aggregation over the entire group/partition. With an order by, there is a logic that follows the sequence of the rows.  
- Calculating over a set of rows related to current row – it circumvents the need for a GROUP BY 
- Specify window: OVER. PARTITION defines group of rows considered before the aggregation starts again for the next partition. ORDER defines the order within the partition  
- Remember that when you are not actually aggregating a column in a window function, we don’t include the column name between the brackets! E.g. row_number and dense_rank are just with ()
- We can have window functions that ignore null values: nvl(last_value(nullif(col2, 0)) IGNORE NULLS OVER (ORDER BY col1), 0) col2
- When you use these values with the right ordering, you don’t actually even need to aggregate anything. You can then use these values e.g. to calculate percentages of total: value / FIRST VALUE (ORDER BY DESC). The FIRSt_VALUE when order by DESC is the max value. 
- Note that you can get max value by using a rank/row or similar in a CTE and then select WHERE window function value = 1

### Frame caluse 
To create a more unique window in the window functions we create, we can add a frame clause: Rows between. This indicates we want a moving group, relative to the current row. 
-	UNBOUNDED PRECEDING: start off at the first row of the partition
-	X PRECEDING: start off x rows before the current row
-	CURRENT ROW: start off at the current row
-	X FOLLOWING: start off x rows after the current row

And then: 
-	AND X PRECEDING: end x rows before the current row
-	AND CURRENT ROW: end at the current row
-	AND X FOLLOWING: end x rows after the current row
-	AND UNBOUNDED FOLLOWING: end at the last row of the partition

‘Rows between 5 preceding and current row’ to show between everything between 5 above and current row 

### Window function options
- SUM for running totals: SELECT duration_seconds, SUM(duration_seconds) OVER (ORDER BY start_time) AS running_total
- AVERAGE for moving average: 
- ROW NUMBER: unique row number for each row: SELECT start_terminal, start_time, duration_seconds, ROW_NUMBER() OVER (PARTITION BY start_terminal ORDER BY start_time) AS row_number 
- RANK: similar to row number, but rank will display the same rank for the same value 2 – 2 - 4: SELECT start_terminal, duration_seconds,  RANK() OVER (PARTITION BY start_terminal ORDER BY start_time)AS rank
- DENSE_RANK: similar to rank. Difference: 2 -2 -3. So whereas rank can skip the missing ranks, dense rank will continue where it left off 
- LAG: pull data from previous row SELECT start_terminal, duration_seconds, LAG(duration_seconds, 1) OVER (PARTITION BY start_terminal ORDER BY duration_seconds) AS lag,
- LEAD: pull daat from next row: LEAD(duration_seconds, 1) OVER (PARTITION BY start_terminal ORDER BY duration_seconds) AS lead
- FIRST_VALUE: first value in partition 
- LAST_VALUE: last value in partition

## NULL
- 3 valued logic: True, False, Unknown. X *-+/ NULL = NULL 
- A NULL value in a database is used to signify a missing or an unknown value. NULL by itself is not a value: NULL=NULL actually equals to FALSE. NULL means ‘could be anything’, nothing equals NULL because each NULL is different. This is also why you can’t join on NULLS – it doesn’t return anything because the condition is FALSE. A good thing about NULLs is that they don’t signify any specific value. Therefore, when you aggregate over a column that includes NULL values, these NULL values are not included in the aggregation, and e.g. your AVG equals to what you would realistically expect. So: 
  - NULL values are a distinct GROUP BY function
  - NULL values are not considered in aggregate functions, except count(*)


## Other learning
- Not IN vs NOT EXISTS. When we run a subquery that excludes data in a subquery, we use NOT Exists as NOT IN would equal to NULL whenever a NULL value is returned.  
- Always group by when running an aggregate function. Use having when filtering on aggregates  
- COUNT(*) will include all values, including NULLs, whereas COUNT(column) will only ever count the non null values. With aggregate functions, NULLS are not included in the calculation. This can be tricky: if you AVG(x), it’ll only take the non null values. You want to either replace the NULLS – as the calculation sum(Y) / count(*) will include the NULL values.  
- CONVERT allows to define a format for the converted value, CAST does not. CONVERT(datatype, value, style). E.g. CONVERT(VARCHAR, GETDATE(),101). The styles are formulated as 101, 102 etc. 
- IIF (inline IF): used to return one of two results based on the result of a Boolean condition. IIF(Boolean expression, true value, false value). When TRUE, return true value. Else return false value. Bascially, these functions are shortened CASE statements. 
- Selecting any top 10 results from a dataset only speeds up the process if the query is very simple, otherwise all operations still need to be performed. 
- When using Distinct, use it only once as the first word after SELECT. You can’t use it more often and you’ll always get combinations of unique pairs of the things you are selecting
- When doing calculations, you'll want to use nullif in the denominator 
- Within the order by clause, you can use OFFSET. With this, you select the first X rows to skip in the results set. In conjunction with OFFSET you can use FETCH. FETCH is used to select the next N rows after the offset rows are skipped. 
- Dates 
  -	Round dates to months by dividing day dates by 100. E.g. 20180101 just becomes 201801
  -	The reason why dates are stored YYYYMMDDis because even when stored as a string, it will still order chronically 
  -	Try to use a date calendar table rather than going crazy trying to convert or cast dates. 


## Joins
- A join is used to combine, or join data from more than 1 table. This data is combined into one result 
- The ON clause specifies how the tables relate to each other. So you join all rows from table A on all rows in table B for which the key in table A is the same the key in table B. When there is a match, SQL takes all columns of table A and joins them to all columns of table B for which the join condition is met. The ON clause allows us to match records within different tables. The ON predicate states the matching condition, which records from both tables must have. Here the condition is that the id field from the color table and the color_id field from the shoes table must have matching values. If a record doesn’t have a match, it will be left out of the results.
- Filter in where vs join: where will apply over entire dataset (similar to inner join), on join will only apply to that join 
  - Filter within the ON clause if you want to filter within one specific table before the join actually happens. In this case, we’d return all items from the left table, but only those lines which meet the criteria will have any associated rows 
  - Filter within the where clause when you want to filter after the tables are already joined. This essentially just comes down to doing an inner join. This filter goes over the entire dataset
- Difficulties with joins: 
  - Symmetric aggregates when we introduce more rows into a table 
  - Multiple joins: each join is on a temp table from the join prior 
- Joins where you match using equality (=) are called equi joins. Joins where you don’t match on equality are called non equi-joins (e.g. used when you use >) (also called theta-joins)
- Joins can be done on any comparison operators: BETWEEN, = < >=, <=, LIKE, etc. 
-	Joins can be done to filter as well: JOIN on first_ofmonth loaned = last of month loaned. If this inner join returns a result, you know that that particular loaned was there prior as well as post.  
-	NULL values aren’t equal to another so they won’t join 
-	Every time we join, we basically create a new temporary/derived table, on which we can then further join. The only time the join ON clause actually matters is when we perform the first join. Any subsequent join is basically a join on a derived table from an earlier join and the subsequent JOIN ON clause applies to the derived table, not the initial table. This also means that the results might change: a FULL JOIN after an INNER JOIN only leaves you with results from the derived table with the INNER JOIN, so you might miss out rows if the INNER JOIN condition hasn’t been met. In a similar way, if you inner join more than 1 table, we first eliminate all non matching values between table 1 and 2. This leave us with a temporary table. We then match this temporary table to the new table and again eliminate all non matching columns. 
-	JOIN conditions are applied from top to bottom
-	When you join on a non unique key, your resulting table will have duplicate values. You get around this using only unique keys or by using DISTINCT 

### Join types
-	INNER JOIN: shows all of the intersects between two tables or columns: if table A = 1,2,3,4 and table B is 2,3, an INNER JOIN shows us 2,3. An inner join will combine rows from different tables if the join condition is true/ when the rows match. Just writing JOIN equals to writing INNER JOIN. An inner join is nothing more than a filtered CROSS JOIN, where the filter is applied in a dedicated ON clause.  
-	LEFT (OUTER) JOIN: take all data from the left table. If the right table matches, there’ll be values from the right table. If not, it’ll return NULL. 
-	RIGHT (OUTER) JOIN: take all data from the right table, similar principle as LEFT JOIN 
-	SELF JOIN is another form of join where a table essentially refers to itself. 
-	CROSS JOIN: join every single combination within the tables. You don’t need a join condition here. It returns a Certesian product. It erturns the number of rows in first table multiplied with number of rows in second table. 
-	FULL JOIN – return all values from left and right talbe and if no match is found, return NULLs 
-	Lateral joins: these allow the right hand side to access columns from the left hand side. They operate in essence similar to correlated subqueries, but where a correlated subquery using one row and column, lateral joins can return more rows in still one column. Lateral joins are used using APPLY (OUTER APPLY and CROSS APPLY) keywords in SQL Server. What happens is that we are applying a function to each row of a table and that function produces rows. Example: take an actor and return the average revenue of their top 5 best selling films. With CROSS APPLY, you perform a CROSS JOIN, where the right hand side of the join can reference columns from the left hand side of the join expression. CROSS APPLY can also reference a previous CROSS APPLIED table. 

![Join types](https://user-images.githubusercontent.com/28791247/93736498-77d24c80-fbd8-11ea-88b0-e84c743c66d4.png)

## Set operators
- Set operators allow us to combine results of two queries into a single query.
- Whereas joins can be thought of as horizontal – adding additional columns to a table, UNION adds additional rows to a table.
- UNION: you get each record appearing in either table. 1,2,3,4 and 1,4,5,6 results in 1,2,3,4,5,6. UNION removes duplicated records.
-	UNION ALL: all rows will be added to the initial data source, even when they are duplicate values. Union ALL would result in 1,1,2,3,4,4,5,6
-	When doing a union, you need to make sure that the column names between the different data sets are the same. Another requirement is that the data types between the columns need to be the same 
- You can mask columns to still have a valid UNION statement - e.g. create a string sessions ID unioned to actual session IDs 
- Intersect returns rows that are common between two tables. A more efficient way of doing the same thing is by using an inner join. The only difference is that inner join doesn’t join on NULL values, whereas INTERSECT does match NULL values
-	EXCEPT returns only rows found in the left query or table. – a more efficient way of doing this is using a LEFT OUTER JOIN or a subequery (WHERE SELECT X FROM Y WHERE K IS NULL). The LEFT JOIN here is perhaps slightly less readable, EXCEPT might be preferred 
-	MINUS will display the results of query1 and remove those that match any records from query 2. MINUS is the same as EXCEPT 



## Syntax reminders
- CASE WHEN X = Y THEN Z ELSE NULL END AS X
- CAST(DATETIME AS DATE) AS date 
- DATEDIFF(date part, start value, end value): return the time value between two dates
- DATEADD(date part, number, value): add a date period to a date. If negative, than that date part is substracted. 
- SUM(X) OVER (PARTITION BY ORDER BY) AS: here we are summing a column 
- ROW_NUMBER() OVER (PARTITION BY ORDER BY): we don’t aggregate here – all we do is assign a row number
- LAG(duration_seconds, 1) OVER (PARTITION BY start_terminal ORDER BY duration_seconds) AS lag,
- LEAD(duration_seconds, 1) OVER (PARTITION BY start_terminal ORDER BY duration_seconds) AS lead
- AVG(ad.downloads) OVER(ORDER BY ad.date ROWS BETWEEN 29 PRECEDING AND CURRENT ROW) AS avg_downloads
- WITH CTE_NAME AS (SELECT), 2nd_CTE NAME AS ()

## Other 
- A case statement returns a value based on one or more conditional tests. Remember that the order of operations is top to bottom. The first TRUE event is returned.
- Aggregated functions include sum, count, min, max, avg. They compute a single result set from a set of input values
- HAVING filters summarized grouped by clauses – WHERE filters only individual records. So WHERE is performed before any grouping took place, whereas HAVINg takes place after the grouping
- Filtering on max values: avoid joins for performance reasons. Instead, aim to do a descending row_number window function.
- Derived tables: tables created on the fly using select statements. Derived table expressions appear in the FROM clause of a query. These are limited to outer select and can’t be used further outside the scope of outer select query. Derived tables are often used to get data where an aggregate function is applied: 
SELECT 		loanid, amount
FROM 		a
JOIN 		(SELECT loanid, min(timestamp) FROM B) b ON a.loanid = b.loanid AND a.timestamp = b.timestamp.

## Subquery
-	Subqueries are also called nested queries. The provide a means to combine data from two tables into a single result. They're a SELECT statement nested within another statement. The result of subquery is used to further restrict data – with that a subquery is often in the WHERE clause. Other than the standard nested query, there are also correlated subqueries, which rely on the outer query. 
-	A classic example of a subquery is this: 
SELECT 		name 
FROM 		world 
WHERE 	continent = 'Europe' 
AND GDP/population > 
(SELECT 	GDP/Population 
FROM 		world 
WHERE 	name = 'United Kingdom')
-	Subqueries can be handy, but they are fundamentally inefficient (i.e. they can slow down the query). If you can replace them, do so. However, always check the query plan. Subqueries tend to be slower than the join alternative: a join needs to be executed once, whereas a correlated subquery needs to be executed for every element you are filtering on. A normal subquery replaces a single value that is placed in the WHERE clause so that doesn’t necessarily slow things down too much. A correlated subquery cannot be replaced by a single value as it needs to compare the inner with the outer query. Therefore, this is slower. 
-	Subqueries can be in a SELECT statement. In this case, subqueries can only return one value as they represent a column with corresponding values  
-	Correlated subqueries are when the outer query’s values are incorporated into the subquery’s clauses. E.g. you in the subquery’s WHERE clause you specify WHERE subquery key = outer query key. Another version a correlated subquery is when the subquery uses a table other than the outer query 
- The exists condition is a subquery. The EXISTS condition returns true whenever the subquery returns values. We can also use NOT EXIST: this returns TRUE when 0 rows are returned. Instead of using EXIST, you can also use IN. Both IN and EXIST are also referred to as SEMI JOINs. NOT EXISTS and NOT IN are referred to as ANTI JOINs. EXISTS and IN are the same. There is however a difference between NOT EXISTS and NOT IN. If there is a NULL in any value, NOT IN(X,Y,NULL) will not record any results, because NULL is an unknown value. Because we don’t know whether which ‘value’ equals to unknown, the entire statement for NOT IN becomes unknown. So don’t use NOT IN, use NOT EXISTS instead. In other words: (EXISTS returns TRUE for NULL values, IN returns FALSE for NULL values). Some people will use LEFT JOIN WHERE x IS NULL instead of NOT EXISTS. This however doesn’t really show us of as being an ANTI JOIN and it most likely performs worse than NOT EXISTS. Use this when you want to show X for when Y is or is not the case. You don’t want to use joins here – they are too slow and you might have issues in your query later on.  If you need to check whether you have any matches between a table A and a table B, but you only really care about the results from table A, do make sure you’re using a SEMI-JOIN (i.e. an EXISTS or IN predicate), not an (INNER) JOIN.  Using IN or EXISTS can be done using multiple columns (e.g. WHERE (x,y) IN (u,I)
- We can use the comparison modifiers ANY and ALL to compare a single value to one or more results returned from a subquery.
  - > ANY: greater than one or more items in the list. Equal to: greater than the MIN value of the list 
  - > ALL: only return values when value is greater than ALL values returned by inner query (i.e. value needs to be max value in the list). Rather than use a SELF JOIN on a max value, you can use ALL to return details about a certain ‘max’ value you are trying to get to. 
  SELECT countries.* FROM countries WHERE GPD >= ALL(SELECT GDP FROM countries). This equals to SELECT countries.* FROM countries WHERE GPD = (SELECT MAX(GDP) FROM countries))
  - ANY and ALL are called quantified comparison predicates
-	When we use a subquery in a FROM clause, it is called a derived table (or inline view) as they act as a table that can be used to select columns and join to other tables. First, the subquery is ran and then the results are used as if they represent a table. You can often use JOINs as alternatives, but these derived tables are useful when you e.g. need to use two aggregate functions (e.g. average of sum). They are great for circumventing the logical ordering of SQL clauses. 


## CTEs
-	CTEs are Common Table Expression’. It works as a temporary dataset only available during one session. It is often used to simplify complex queries and increase readability because of the introduced hierarchy. The basic structure is: WITH CTE_NAME AS (SELECT X,Y,Z).You can reference back (i.e. SELECT FROM) the created CTE. It works just like a subquery 
- Benefits of CTEs: 
  - Code becomes a lot more readable 
  - CTEs are easier to debug -
- Recursive CTEs reference themselves. In these cases, the initial CTE is repeatedly executed, returning subsets or data until the complete result is returned. Recursive SQL always uses a UNION ALL between two subqueries, where the initial subquery generates the seed rows and the second subquery generates the recursion from the seed rows. Irts great to use in combination with hierarchical data 

WITH RECURSIVE t(v) AS (
  SELECT 1     -- Seed Row
  UNION ALL
  SELECT v + 1 -- Recursion
  FROM t
)
SELECT v
FROM t
LIMIT 5

WITH all_workers
AS
(
   SELECT Id, BossId, FirstName, LastName, 0 as Org_Level 
   FROM Employees
   WHERE BossId is NULL
   UNION ALL
   SELECT e.Id, e.BossId, e.FirstName, e.LastName, Org_Level + 1
   FROM Employees e INNER JOIN all_workers r 
   ON e.BossId = r.Id
)
SELECT * FROM all_workers	
This recursive CTE first selects the highest arnked employee (they don’t have a boss – which is indicated by a boss Id of NULL) and set this to ORG level 0. Note that the highest boss is simply also an employee. The employee ID in the seed query (i.e. the highest ranked employee) is the boss ID in the employee query (this is going down one layer in the org chart and the highest ranked employee will have employee is his or her team). The seed part of the query remains there – the magic happens in the recursive part. Beacuse each employee is also a boss, we go further and further down the org chart until all employees are also considered as a boss and then all recursive query options have been executed. In the recursive elements, we correlate the result from the initial query and we incremement Org Level by 1 each time. 

![Recursive CTE 1](https://user-images.githubusercontent.com/28791247/93736100-35f4d680-fbd7-11ea-9177-4069a5a5cce1.png)

![Recursive CTE 2](https://user-images.githubusercontent.com/28791247/93736135-473de300-fbd7-11ea-890d-07ec70ae8a11.png)



## Functions
- Roundling functions: 
  - CEILING and FLOOR to return to the next lowest or next highest integer. 
  - ROUND to a number of decimals ROUND(variable, number of decimals to round to). Round to the nearest 1000 using round -3. 
- Signs functions: ABS to obtain the absolute difference between values. This gets rid of any negative value and is useful for doing comparisions.
- String functions: 
  - Position functions: LEN: return the number of characters in a string
  - LEFT and RIGHT: return either the beginning or ending part of a string
  - SUBSTRING: return part of the string (usually a middle part, not the beginiing nor the ending) 
  - UPPER and LOWER: return values whose characters are all-in lower or upper case. 
  - REPLACE: find characters in a string and replace these with other characters
  - MID: retrieve characters in the middle part of a string 
  - TRIM: when you want to get rid of characters from a string at the beginning, end, or both sides of the string
- Other functions
  -	CONCAT – combine strings/characters together. 
  -	COALESCE – when you want to transfer NULL values into actual values. COALESCE takes a list of columns, and returns the value of the first column that is not null. You can also use COALESCE(X,0). This means that if the value is null, you replace it with 0, which equals to using ifnull. 
- Date functions
  - GETDATE(): return the current date
  -	DATENAME (date part, value). There is plenty of to retrieve dateparts (year, month, quaryer, dat, dayofyear, hour, etc.)
  -	DATEPART: similar to datename, but it would return 7 instead of ‘July’. Same results can be obtained using just YEAR(), DAY(), or MONTH()
  -	DATEDIFF(date part, start value, end value): return the time value between two dates
  -	DATEADD(date part, number, value): add a date period to a date. If negative, than that date part is substracted. 
  -	EXTRACT - to take date extracts (e.g. year, month, date) from a date format
  -	DATE_TRUNC: when you are looking to specify all dates/timestamps as a first of a specific time period







## Conversions
- Implicit conversions. These happen automatically (i.e. no CAST or CONVERT functions are used). Example: multiple an INT with a FLOAT (2 decimals). The implicit conversion returns a float with 2 decimals. This is determined by type precedence, which determines the direction or order in which implicit conversions occur. Data types of low precedence will convert to one of higher (high is datetime and float). Be ware that not all data types can be converted. Also, you can’t convert a higher precedence data type to a lower precedence 
- Explicit conversions. When implicit conversions don’t work, we need explicit conversions. This is done using CAST or CONVERT
  - CAST: CAST(value as datatype) (E.g. GETDATE() AS VARCHAR. CAST( AS DECIMAL (10,2)). 10 = a max total of 10 numbers. 2 = 2 decimals after the comma
  - CONVERT allows to define a format for the converted value, CAST does not. CONVERT(datatype, value, style). E.g. CONVERT(VARCHAR, GETDATE(),101). The styles are formulated as 101, 102 etc. 



## Basic Operators
-	= : to determine is something is equal to something else
-	!= or <> : not equal to: on expression is not equal to another expression 
-	> : greater than 
-	>= : greater than or equal to
-	< : less than
-	<= : less than or qual to

## Logical operators 
-	IN() statement – use this when you have multiple values in the where clause. It is basically having multiple OR statements. 
-	BETWEEN statement: used when you specify outer bounds (a range) in a where clause BETWEEN 20180101 and 20180701. This is from up to and including. Prefer using multiple clauses with <= and >=. Reason: BETWEEN is behaving odd when it comes to actual timestamps. 
-	LIKE: when you want to find a specific part of a string: LIKE ‘%thisname’. This is often called pattern matching. You could also use other wildcard characters, such as _: like ‘Se_ven’
-	AND/OR. AND allows you to select only rows that satisfy two conditions. OR allows you to select rows that satisfy either of two conditions. With these, be very careful about where you place the brackets. There is a function in SQL called Exclusive OR. This means that it can be 1 or the other, but never can it be both. With AND/Or, be careful with NULL values. As soon as a NULL value is involved, be awre that nothing equals to NULL and that everything that involves NULL will equal to FALSE.  
-	NOT allows you to select rows that do not match a certain condition
-	Whenever multiple logical operators are used, the results need to be true in order for results to return. 




## Approach to challenges/ interview questions
1. Understand the context and the question 
- Look at the samples provided – do I understand the outcome? Reverse engineer the logic and see if you agree. 
- See if there are any indications of what to do in case of exceptions 
2. Consider the data 
- Consider the relationship cardinality between tables. E.g. 1-1, many to one or many to many. Act accordingly  
- Consider the referential integrity: does a FK always lead to a PK elsewhere, or can left have a key that’s not in right? Decide on LEFT / INNER join 
- Can any table contain NULLs? If so, it would also impact aggregate functions
- Confirm whether the data is unique. If there are duplicates, we need to act accordingly. 
- Always ask whether there is any reason why the data might not be clean 
3. Helpful tips: 
- In the SQL editor pane, write down key notes of the results you need and the specific cases that are implied from the sample questions
- Break the queries down – ideally, you get multiple CTEs that finally make up the end result. Whilst you’re building the query, keep referring to the requirements to ensure you’re building the right thing
- Generally, you’d want to also have a dim date to join on. If you don’t: 
  - Date from timestamp: to_date(‘timestamp’) AS date_1
  - Date_trunc(‘YEAR’,’MONTH’,’WEEK’, ’DAY’, date_1) AS X
4. Technical
- We’re looking for top 3: can some have the same number of books? If so, who goes in top 3? 
- Be careful with <> / NOT IN. Remember that <> will not include nulls: it should become <> OR X IS NULL. And if NOT IN is used – if there is a NULL in the dataset, the whole query would return NULL. Instead, use NOT EXISTS 
- Whenever you use a window function, make sure all data is selected – otherwise you don’t have a window to work with. This means in that in the first CTE where the data is aggregated, you’ll need to group by multiple columns at first 
5. Before final delivery: 
- Did we answer the question?
- Do we work properly around the edge cases? 
- Is my style good? 
  - Do I include the right aliases (in join and select and group by and where)? 
  - Do I group by if there are aggregates? 
  - Are my column names correct?
  - Did I order according to the requirements?

## Data modification language 
- CRUD = Create, Read, Update and Delete: the four basic functions of persistent storage that are often employed by SQL. 
- DDL = Data Definition Language. This is used to define the structure of database and objects: CREATE, ALTER, DROP, TRUNCATE, COMMENT, RANAME. DDL statements cannot be rolled back as they have a COMMIt in their execution. 
- DML = Data Manipulation Language, allow us to change or manipulate daat. SELECT, INSERT, UPDATE, DELETE, MERGE. DML statements can be rolled back
-	DCL: Data Control Language. GRANT, REVOKE 
-	TCL: Transaction Control Language. Used to manage changes made by DML statements. COMMIT, ROLLBACK 
- The SELECT, INSERT, UPDATE, DELETE and MERGE statements are collectively referred to as Data Manipulation Language (DML) statements. These statements allow us to view and modify data 
- What is inside the clause are called parameters, list of columns, data types, or values that are passed to a clause as an argument
- CREATE TABLE  (CREATE TABLE celebs (id INTEGER PRIMARY KEY, name TEXT, age INTEGER)
- INSERT INTO: INSERT INTO celebs (id, name, age) 
VALUES (1, 'Justin Bieber', 21);
This inserts new rows into a table. To test these statements you can BEGIN TRANSACTION then have your insert statement and then use ROLLBACK. If you’re happy with the results, you use COMMIT rather than ROLLBACK. When you insert data from another table, you’d use INSERT INTO SELECT … 
- UPDATE: UPDATE celebs
SET age = 22
WHERE id = 1;
This edits the row where the id = 1 and the thing to edit is that the age changes to 22. Similar to INSERT, you can either COMMIT or ROLLBACK any changes you made. With UPDATE statements, also make sure you are updating the correct rows; the WHERE clauses is of high importance here  
- ALTER: ALTER TABLE celebs ADD COLUMN twitter_handle TEXT;
This adds a new column to the table. 
- DELETE: DELETE FROM celebs WHERE twitter_handle IS NULL; 
This deletes one or more rows from a table (use COMMIT or ROLLBACK). The DELETE statement logs all rows being deleted, making it a bit easier to recover from mistakes. To delete all rows in a table, use TRUNCATE TABLE. It is much faster than DELETE but remember than it just deletes all data present in a specific table. 
- MERGE: merge allows to INSERT< UPDATE, or DELETE on one table based on source data from another. MERGE targetTable
USING sourceTable
ON joinCondition
WHEN MATCHED  --update
WHEN NOT MATCHED --insert
WHEN NOT MATCHED SOURCE –delete
Using MERGE eliminates the need for having multiple individual statements for each operations. WE INSERT, UPDATE or DELETE on the target table, using the source table as input. Note that MERGE should only be used in more complex scenarios as it is more complex and probably runs less efficiently. It works best when there are different matching conditions that need to be applied. 	
- DECLARE @tablename table(column1 date type, column2 datatype, etc) : define a table using @.  
- OUTPUT: the OUPUT clause is used to log changes made to rows.Once you have a table variable set up, you can use OUTPUT INTO @UPDATELOG (@UPDATELOG is defined using DECLARE). Now you’re logging the results. 

## Data types
Data types define the characteristics of the data stored (test, integers, dates, floats, etc)
- INT: used to store whole numbers. This type can be used in calculations
- VARCHAR: store variable length text values. You define how many maximal characters are stored in the column definition. If a value takes less characters, it only allocates enough space to hold these characters. This makes VARCHAR very popular 
- DATETIME: used to store date and time. We can manipulate these dates with SQL’s built in functions. 
- DECIMAL (and FLOAT): datatypes that support decimal values 
- BIT – use this when you need to store Boolean values. 
- SQL does support many more data types


## QA in SQL 
- Run a larger SQL query
- Test the results of the query using smaller SQL statements
- Check for counts accross different CTEs. Use COUNT(*)
- Check for NULL values 
- Always sanity check the results 
- Take a very small subset of data or even individual examples and see what happens 
- EDA the results in python

## Glossary 
-	SQL = Structured Query Language. It is the language used to communicate with a database.
- Databases: sets of related tables all centered around a central topic or purpose3
- Storage Engine: manages how data is store in the database. Responsible for all aspects of ACID (Atomic, Concurrency, Isolation, and Durability) 
  - Atomic: either we save all data, or none when two or more pieces of data are involved in a transaction
  - Consistent: data stored can’t violate any of the database’s integrity: interrupted changes are rolled back. Consistency means that any transaction will bring the database from one consistent state to another. Data must be valid according to all business rules.
  - Isolation: transaction in question is not affected by any other transaction taking place. 
  - Durable: once a transaction is committed, it will remain so, regardless of a subsequent system failure 
- Tables: used to store data within the database 
- Data modelling is about designing a database. An entity is a data model.
- A database schema represents all tables of a database as well as the relationships between them. 
-	A relational database is a database that organizes information into one or more tables. 
-	A table is a collection of data organized into rows and columns. Tables are sometimes referred to as relations. Each table has one unique primary key. 
-	A column is a set of data values of a particular type.
-	A row is a single record in a table
-	Columns in a table are called dimensions or attributes. The values that make up the dimensions are called measures or simply values  
-	Variables - this is where you can define a variable once and then use that variable throughout the query. Example: a query uses multiple dates. Set a variable name equal to a date and use the variable name throughout the query. This is a much better way than manually plugging in the dates after. In Snowflake, variables are set using the SET keyword. When you reference the variables after, use the prefix $ in front of the variables within the actual query 


## Stored procedures
Stored Procedures: programs (written in programming languages) that solve a problem that couldn’t be solved using a query. They are group of one or more database statements stored in the data dictionary. A stored procedure is a way for you to store a set of SQL statements and accompanying programming statements within the database and run them later. This means we can combine computer programming languages with SQL. SQL isn’t capable of solving all problems, but when combined with other programming languages, this becomes a possibility. A procedure is a set of instructions used to perform an action. Within SPs we can also have IF ELSE statements, as well as dynamic SQL, which is SQL created and executed at run-time. This implies that we first have variables set and then we execute these variables in the query (this is using DECLARE @). We use SPs rather than normal queries: they are optimized for execution (and the best version is cached for later use. They are executed using a ingle line of code rather than using hundreds on line of code of the queries. Better security.  

A stored procedure is a set of SQL statements that can be executed on the database. It is stored as a object in the database.
A stored procedure allows for code that is run many times to be saved on the database and run at a later time, making it easier for yourself and other developers in the future.
It also allows for extra features that aren’t available in regular SQL language to be used, such as loops, output, and manipulation variables.

The alternatives to using SP is to have the code stored in the application or in normal SQL scripts 
Benefits of using stored procedures:
- Security: applications access the SP and there is access control. Also, it can guard against SQL injection
- Easier to maintain and tune: code stored in SP easier to dig into than code stored in application
- Business logic in one place: database stores data for many different applications. This means code is reusable and other applications can have access to it  

A SP has three main parts:
-	Inputs: SPs can accepts parameter values as inputs (these are the inputs to a function)
-	Execution: execute SQL statements, utilize IF THEN logic (or CASE) and use loops. Also able to call another stored procedure. They can also use cursors (allow us to access results row by row). 
-	Outputs: whatever values to be returned are 