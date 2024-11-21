#### What is a foreign key, and how do you define one?
- A foreign key links one table to another, ensuring referential integrity

```code
CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

#### 2. What is the difference between `CHAR` and `VARCHAR`?
- `CHAR` - Fixed-length. E.g., `CHAR(5)` always stores 5 characters.
- `VARCHAR`: Variable-length. E.g., `VARCHAR(5)` stores up to 5 characters.

#### 3. How do you fetch top N records from a table?

```code
SELECT * FROM Employees ORDER BY Salary DESC LIMIT 5; -- MySQL
```

```code
SELECT TOP 5 * FROM Employees ORDER BY Salary DESC; -- SQL Server
```

#### 4. What is the difference between `CROSS JOIN` and `INNER JOIN`?
- `CROSS JOIN` - Returns the Cartesian product (all combinations of rows)
- `INNER JOIN` - Returns rows where there is a match

#### 5. Write a query to find all employees who earn more than the average salary?

```code
SELECT * 
FROM Employees
WHERE Salary > (SELECT AVG(Salary) FROM Employees);
```

#### 6.What are aggregate functions? Provide examples.
- Aggregate functions perform calculations on a group of values
- Examples: `SUM`, `COUNT`, `AVG`, `MAX`, `MIN`

```code
SELECT COUNT(*) AS TotalEmployees, AVG(Salary) AS AverageSalary FROM Employees;
```

#### 7. What are subqueries, and where can you use them?
- A query nested inside another query
- Can be used in `SELECT`, `WHERE`, `FROM`, or `HAVING`

```code
SELECT Name 
FROM Employees
WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE Location = 'New York');
```

#### 8. What is a `view` in SQL?
- A virtual table based on a query

```code
CREATE VIEW HighSalaryEmployees AS 
SELECT Name, Salary 
FROM Employees 
WHERE Salary > 50000;
```

#### 9. How do you find the nth highest salary?

```code
SELECT DISTINCT Salary 
FROM Employees 
ORDER BY Salary DESC
LIMIT 1 OFFSET n-1; -- Replace n with the desired rank
```

#### 10. What is a `self join`?
- A join where a table is joined with itself

```code
SELECT A.Name AS Employee, B.Name AS Manager
FROM Employees A
INNER JOIN Employees B ON A.ManagerID = B.EmployeeID;
```

#### 11. What are triggers in SQL?
- A trigger is an action executed automatically when a specific event occurs

```code
CREATE TRIGGER BeforeInsertTrigger
BEFORE INSERT ON Employees
FOR EACH ROW
SET NEW.CreatedAt = NOW();
```

#### 12. What is the difference between ROW_NUMBER(), RANK(), and DENSE_RANK()?
- **`ROW_NUMBER()`** - Assigns a unique rank
- **`RANK()`** - Assigns ranks but skips numbers for ties
- **`DENSE_RANK()`** - Assigns ranks without skipping numbers

#### 13. What is the use of `CASE` statements?

```code
SELECT Name, 
       CASE 
           WHEN Salary > 50000 THEN 'High'
           WHEN Salary > 30000 THEN 'Medium'
           ELSE 'Low'
       END AS SalaryCategory
FROM Employees;
```

#### 14. What is a stored procedure? How do you create one?
- A reusable SQL block stored in the database

```code
CREATE PROCEDURE GetHighSalaryEmployees ()
BEGIN
    SELECT * FROM Employees WHERE Salary > 50000;
END;
```

#### 15. Explain the difference between `ANY` and `ALL` operators
- `ANY` - Compares a value with any value in a subquery
- `ALL` - Compares a value with all values in a subquery

```code
SELECT * FROM Employees WHERE Salary > ANY (SELECT Salary FROM Employees WHERE DepartmentID = 1);
```






