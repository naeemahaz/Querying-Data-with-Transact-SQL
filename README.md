# Querying-Data-with-Transact-SQL

Key Points
Transact-SQL is the language used to query data in Microsoft SQL Server and Azure SQL Database.
Data is stored in tables, which may be related to one another through common key fields.
Objects in a database are organized into schemas.
The fully qualified naming syntax for an object is server_name.database_name.schema_name.object_name, but in most cases you can abbreviate this to schema_name.object_name.

Key Points
Use the SELECT statement to retrieve a rowset of data from tables and views in a database.
SELECT statements are written with the following clauses: SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY. However, the query engine processes the clauses in this order: FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY.
In the SELECT clause, you can use * to return all columns, but generally you should specify explicit columns.
You can specify expressions in the SELECT clause to return the results of calculations.
You can use the AS keyword to specify aliases for columns in the rowset returned by the SELECT statement.

Key Points
Transact-SQL supports a wide range of data types, which can be broadly categorized as exact numeric, approximate numeric, character, date/time, binary, and other (which includes specialized data types for handling data such as XML and spatial data).
Some data types are compatible, and values can be implicitly converted between them. Conversion between other data types requires the use of explicit conversion functions.

Key Points
NULL is used to indicate an unknown or missing value. NULL is not equivalent to zero or an empty string.
Arithmetic or string concatenation operations involving one or more NULL operands return NULL. For example, 12 + NULL = NULL.
If you need to compare a value to NULL, use the IS operator instead of the = operator. 
The ISNULL function returns a specified alternative value for NULL columns and variables.
The NULLIF function returns NULL when a column or variable contains a specified value.
The COALESCE function returns the first non-NULL value in a specified list of columns or variables).

Key Points
By default, the SELECT statement returns all rows. If mulitple rows contain the same values for every column, they are duplicated in the results. Using the DISTINCT keyword eliminates duplicates, ensuring that only one row for each distinct combination of column values is returned.
The order of rows in the result of a SELECT statement is not guaranteed unless you explicitly specify one or more columns in an ORDER BY clause. You can specify sort direction as ASC (the default) or DESC.
You can combine the ORDER BY clause with the TOP keyword to retrict the results so that they include only the top n rows (where n is the number or percentage of rows you want to return).
You can implement a query to retrieve a specified "page" of results by using the OFFSET and FETCH keywords with the ORDER BY clause.

Key Points
Use the WHERE clause to filter the results returned by a SELECT query based on a search condition.
A search condition is composed of one or more predicates.
Predicates include conditional operators (such as =, >, and <), IN, LIKE, and NOT.
You can use AND and OR to combine predicates based on Boolean logic.

Key Points
Joins are used to match rows in one table to rows in another table.
The query engine supports two ways to define joins: the ANSI SQL-92 syntax (in which the join is specified in the FROM clause) and the older ANSI SQL-89 syntax (in which the join is specified in the WHERE clause). The ANSI SQL-92 syntax is the preferred approach.

Key Points
Inner joins return only rows where a match can be found in both tables.
Inner joins that match rows based on columns containing the same value in both tables are sometimes referred to as equi-joins.

Key Points
Use a Left Outer Join to include all rows from the first table and values from matched rows in the second table. Columns in the second table for which no matching rows exist are populated with NULLs.
Use a Right Outer Join to include all rows from the second table and values from matched rows in the first table. Columns in the first table for which no matching rows exist are populated with NULLs.
Use a Full Outer Join to include all rows from the first and second tables. Columns in the either table for which no matching rows exist are populated with NULLs.

Key Points
A cross join returns a Cartesian product that includes every combination of the selected columns from both tables.
While not commonly used in typical application processing, cross joins can be useful in some specialized scenarios - such as generating test data.

KEY POINTS
A self-join is an inner, outer, or cross join that matches rows in a table to other rows in the same table. 
When defining a self-join, you must specify an alias for at least one instance of the table being joined.

Key Points
Use UNION to combine the rowsets returned by mulitple queries.
Each unioned query must return the same number of columns with compatible data types.
By default, UNION eliminates duplicate rows. Specify the ALL option to include duplicates (or to avoid the overhead of checking for duplicates when you know in advance that there are none). 

Key Points
Use INTERSECT to return only rows that are returned by both queries.
Use EXCEPT to return rows from the first query that are not returned by the second query.

Key PointS
Scalar functions return a single value based on zero or more input parameters.
Logical functions return Boolean values (true or false) based on an expression or column value.
Window functions are used to rank rows across partitions or "windows". Window functions include RANK, DENSE_RANK, NTILE, and ROW_NUMBER.
Aggregate functions are used to provide summary values for mulitple rows - for example, the total cost of products or the maximum number of items in an order. Commonly used aggregate functions include SUM, COUNT, MIN, MAX, and AVG.

Key Points
You can use GROUP BY with aggregate functions to return aggregations grouped by one or more columns or expressions.
All columns in the SELECT clause that are not aggregate function expressions must be included in a GROUP BY clause.
The order in which columns or expressions are listed in the GROUP BY clause determines the grouping hierarchy.
You can filter the groups that are included in the query results by specifying a HAVING clause.

Key Points
Subqueries are Transact-SQL queries nested within an outer query.
Scalar subqueries return a single value.
Multi-valued subqueries return a single-column rowset.

Key Points
Correlated subqueries reference objects in the outer query.

Key Points
The APPLY operator enables you to execute a table-valued function for each row in a rowset returned by a SELECT statement. Conceptually, this approach is similar to a correlated subquery.
CROSS APPLY returns matching rows, similar to an inner join. OUTER APPLY returns all rows in the original SELECT query results with NULL values for rows where no match was found.

Key Points
Views are database objects that encapsulate SELECT queries.
You can query a view in the same way as a table, however there are some considerations for updating them.

Key Points
Temporary tables are prefixed with a # symbol (You can also create global temporary tables that can be accessed by other processes by prefixing the name with ##)
Local temporary tables are automatically deleted when the session in which they were created ends. Global temporary tables are deleted when the last user sessions referencing them is closed.
Table variables are prefixed with a @ symbol.
Table variables are scoped to the batch in which they are created.

Key Points
Table-Valued Functions (TVFs) are functions that return a rowset.
TVFs can be parameterized.

Key Points
A derived table is a subquery that generates a multicolumn rowset. You must use the AS clause to define an alias for a derived query.
Common Table Expressions (CTEs) provide a more intuitive syntax or defining rowsets than derived tables, and can be used mulitple times in the same query.
You can use CTEs to define recursive queries.

Key Points
Use GROUPING SETS to define custom groupings.
Use ROLLUP to include subtotals and a grand total for hierarchical groupings.
Use CUBE to include all possible groupings.

Key Points
Use PIVOT to re-orient a rowset by generating mulitple columns from values in a single column.
Use UNPIVOT to re-orient mulitple columns in a an existing rowset into a single column.

Key Points
Use the INSERT statement to insert one or more rows into a table.
When inserting explicit values, you can omit identity columns, columns that allow NULLs, and columns on which a default constraint is defined.
Identity columns generate a unique integer identifier for each row. You can also use a sequence to generate unique values that can be used in multiple tables.

Key Points
Use the UPDATE statement to modify the values of one or more columns in specified rows of a table.
Use the DELETE statement to delete specified rows in a table.
Use the MERGE statement to insert, update, and delete rows in a target table based on data in a source table.

Key Points
A batch defines a group of Transact-SQL command submitted by a client application for execution. Some commands can only be executed at the start of a new batch, and variable values cannot span batches.
Use comments to document your Transact-SQL code. Inline comments are prefixed by --, and multi-line comment blocks are enclosed in /* and */.
Declare variables by using the DECLARE keyword, specifying a name (prefixed with @) and a data type. You can optionally assign an initial value.
Assign values to variables by using the SET keyword or in a SELECT statement.

Key Points
Use the IF keyword to execute a task based on the results of a conditional test.
Use an ELSE clause if you need to execute an alternative task if the conditional test returns false.
Enclose mulitple statements in an IF or ELSE clause between BEGIN and END keywords.

Key Points
Use a WHILE loop if you need to repeat one or more statements until a specified condition is true.
Use BREAK and CONTINUE to exit or restart the loop.
Avoid using loops to iteratively update or retrieve single records - in most cases, you should use set-based operations to retrieve and modify data.

Key Points
Use stored procedures to encapsulate Transact-SQL code in a reusable database objects.
You can define parameters for a stored procedure, and use them as variables in the Transact-SQL code it contains.
Stored procedures can return rowsets (usually the results of a SELECT statement). They can also return output parameters, and they always return a return value, which is used to indicate status.

Key Points
System errors have pre-defined numbers, messages, severity levels, and other characteristics that you can use to troubleshoot issues.
You can use RAISERROR and THROW to raise custom errors.

Key Points
Use TRY...CATCH blocks in your Transact-SQL code to catch and handle exceptions.
A common exception handling pattern is to log the error, and then if the operation cannot be completed successfully, throw it (or a new custom error) to the calling application.

Key Points
Transactions are used to protect data integrity by ensuring that all data changes within a transaction succeed or fail as a unit.
Individual Transact-SQL statements are inherently treated as transactions, and you can define explicit transactions that encompass mulitple statements.
Use the BEGIN TRANSACTION, COMMIT TRANSACTION, and ROLLBACK TRANSACTION statements to manage transactions.
Enable the XACT_ABORT option to automatically rollback all transactions if an exception occurs.
Use the @@TRANCOUNT system variable and XACT_STATE system function to determine transaction status.

