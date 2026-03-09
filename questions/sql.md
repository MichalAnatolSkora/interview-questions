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
*   **Indexes:** Explain the difference between a clustered and a non-clustered index.
