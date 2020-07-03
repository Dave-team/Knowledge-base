# SQL

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