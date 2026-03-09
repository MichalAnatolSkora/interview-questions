# SQL and Databases Interview Questions

## Relational Databases & SQL
*   **Keys:** What is a primary key? What is a foreign key? Can a single table have foreign keys on multiple columns?
*   **Views:** What is a view?
*   **Stored Procedures vs Functions:** What is a stored procedure? What is the main difference between a stored procedure and a function?
*   **Grouping:** What is the `GROUP BY` clause? In what cases do we use it?
*   **Query Hints:** What is `WITH(NOLOCK)` in SQL Server?
    *   *Note:* It is used in `SELECT` statements to prevent taking shared locks, thus avoiding deadlocks and not waiting for other queries to complete, though it can read uncommitted "dirty" data.
*   **Triggers:** What is a trigger?
*   **Temporary Data Storage:** Explain the differences between:
    *   Temporary table (session scope)
    *   Table variable (local scope)
    *   Common Table Expression - CTE (local scope)
*   **Joins:** What are the different types of `JOIN`s in SQL and what do they do?
    *   *Answer:* 
        *   `INNER JOIN`: Returns records that have matching values in both tables.
        *   `LEFT (OUTER) JOIN`: Returns all records from the left table, and the matched records from the right table.
        *   `RIGHT (OUTER) JOIN`: Returns all records from the right table, and the matched records from the left table.
        *   `FULL (OUTER) JOIN`: Returns all records when there is a match in either left or right table.
        *   `CROSS JOIN`: Returns the Cartesian product of the two tables (every row from the first table paired with every row from the second table).
*   **Indexes:** What are indexes? Explain the difference between a clustered and a non-clustered index.
    *   *Answer:* An index is an on-disk structure associated with a table or view that speeds up retrieval of rows. A **Clustered Index** determines the physical order of data in a table (so there can only be one per table). A **Non-Clustered Index** contains pointers to the physical data rows (you can have many per table).
*   **Included Columns in Indexes:** Can you have a column in an index that is not used for searching (in the `WHERE` clause)?
    *   *Answer:* Yes, you can add "Included Columns" to a non-clustered index. These columns are not part of the physical index tree (so they aren't used for sorting/searching), but they are attached to the leaf nodes. This is useful for "covering queries" – if your `SELECT` query only asks for columns present in the index (as key or included columns), SQL Server can satisfy the query entirely from the index without having to look up the actual data row (Key Lookup), improving performance.
