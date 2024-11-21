#### 1. What is SQL? Explain its types.
- SQL (Structured Query Language) is used to interact with relational databases
- **Types**
    - DDL (Data Definition Language): Defines schema (`CREATE`, `ALTER`, `DROP`)
    - DML (Data Manipulation Language): Modifies data (`INSERT`, `UPDATE`, `DELETE`)
    - DQL (Data Query Language): Queries data (`SELECT`)
    - TCL (Transaction Control Language): Manages transactions (`COMMIT`, `ROLLBACK`)
    - DCL (Data Control Language): Manages permissions (`GRANT`, `REVOKE`)

#### 2. Write a query to fetch all records from a table.
```code
SELECT * FROM table_name;
```

#### 3. How do you create a new table?
Defines table Employees with columns and their data types

```code
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50),
    Age INT,
    Salary DECIMAL(10,2)
);
```

#### 4. What is the difference between WHERE and HAVING?
- **WHERE** - Filters rows before grouping
- **HAVING** - Filters groups after aggregation

```code
SELECT Department, AVG(Salary) 
FROM Employees
WHERE Age > 25
GROUP BY Department
HAVING AVG(Salary) > 50000;
```

#### 5. Write a query to insert data into a table?

```code
INSERT INTO Employees (EmployeeID, Name, Age, Salary)
VALUES (1, 'John Doe', 30, 55000.00);
```

#### 6. What is the difference between DELETE and TRUNCATE?

- `DELETE` - Removes specific rows; can use a WHERE clause; logged operation
- `TRUNCATE` - Removes all rows; faster; cannot use a WHERE clause

#### 7. Write a query to update a record in a table?

```code
UPDATE Employees SET Salary = 60000 WHERE EmployeeID = 1;
```

#### 8. How do you delete a record from a table?

```code
DELETE FROM Employees WHERE EmployeeID = 1;
```

#### 9. What is a `PRIMARY KEY`?
- A `PRIMARY KEY` uniquely identifies each record and cannot contain NULL values

```code
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

#### 10. What is the difference between `INNER JOIN` and `OUTER JOIN`?
- `INNER JOIN` - Returns matching records
- `OUTER JOIN` - Returns matching and non-matching records (left, right, or full)

```code
SELECT e.Name, d.DepartmentName
FROM Employees e
INNER JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

#### 11. How do you fetch unique values from a column?

```code
SELECT DISTINCT Department FROM Employees;
```

#### 12. What is the use of `GROUP BY`?
- Groups rows with the same values and allows aggregation

```code
SELECT Department, COUNT(*) FROM Employees GROUP BY Department;
```

#### 13. How do you sort data in ascending or descending order?

```code
SELECT * FROM Employees ORDER BY Salary ASC; -- Ascending
SELECT * FROM Employees ORDER BY Salary DESC; -- Descending
```

#### 14. What is the use of LIKE in SQL?
- Filters data based on patterns

```code
SELECT * FROM Employees WHERE Name LIKE 'J%'; -- Names starting with 'J'
```

#### 15. How do you find the total salary of employees?

```code
SELECT SUM(Salary) AS TotalSalary FROM Employees;
```

#### 16. What is the difference between `UNION` and `UNION ALL`?
- `UNION` - Combines results, removes duplicates
- `UNION ALL` - Combines results, retains duplicates

```code
SELECT Name FROM Employees UNION SELECT Name FROM Managers;
```

#### 17. How do you find the highest salary in a table?

```code
SELECT MAX(Salary) AS HighestSalary FROM Employees;
```

#### 18. How do you find duplicate rows in a table?

```code
SELECT Name, COUNT(*) FROM Employees GROUP BY Name HAVING COUNT(*) > 1;
```

#### 19. Write a query to fetch the second-highest salary?

```code
SELECT MAX(Salary) AS SecondHighest
FROM Employees
WHERE Salary < (SELECT MAX(Salary) FROM Employees);
```

#### 20. What is the difference between `IS NULL` and `IS NOT NULL`?
- **`IS NULL`** - Checks for NULL values
- **`IS NOT NULL`** - Checks for non-NULL values

```code
SELECT * FROM Employees WHERE Age IS NULL;
```








