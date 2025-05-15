# SQL JOINs and Types

SQL JOINs are used to combine rows from two or more tables, based on a related column between them.

## Example Tables

**Customers**

| CustomerID | FirstName | LastName | Email               | City        |
| ---------- | --------- | -------- | ------------------- | ----------- |
| 1          | John      | Doe      | john@example.com    | New York    |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles |
| 3          | Alice     | Brown    | alice@example.com   | Chicago     |
| 4          | Michael   | Johnson  | michael@example.com | Houston     |
| 5          | Emily     | Davis    | emily@example.com   | Phoenix     |
| 6          | Chris     | Wilson   | chris@example.com   | Miami       |
| 7          | Emma      | Garcia   | emma@example.com    | Seattle     |
| 8          | Daniel    | Martinez | daniel@example.com  | Denver      |

**Books**

| BookID | Title                  | Author              | Price | PublishedYear |
| ------ | ---------------------- | ------------------- | ----- | ------------- |
| 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
| 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
| 3      | 1984                   | George Orwell       | 8.99  | 1949          |
| 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |
| 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |

**Orders**

| OrderID | CustomerID | BookID | Quantity | OrderDate  |
| ------- | ---------- | ------ | -------- | ---------- |
| 1       | 1          | 2      | 1        | 2024-05-01 |
| 2       | 2          | 1      | 2        | 2024-05-03 |
| 3       | 3          | 3      | 1        | 2024-05-05 |
| 4       | 4          | 4      | 3        | 2024-05-06 |
| 5       | 5          | 5      | 2        | 2024-05-07 |
| 6       | 6          | 2      | 1        | 2024-05-08 |
| 7       | 7          | 3      | 4        | 2024-05-09 |

---

## 1. INNER JOIN

Returns records that have matching values in both tables.

```SQL
SELECT Customers.FirstName, Books.Title, Orders.Quantity
FROM Orders
INNER JOIN Customers ON Orders.CustomerID = Customers.CustomerID
INNER JOIN Books ON Orders.BookID = Books.BookID;
```
| FirstName | Title                 | Quantity |
| --------- | --------------------- | -------- |
| John      | To Kill a Mockingbird | 1        |
| Jane      | The Great Gatsby      | 2        |
| Alice     | 1984                  | 1        |
| Michael   | The Catcher in the Rye| 3        |
| Emily     | The Hobbit            | 2        |
| Chris     | To Kill a Mockingbird | 1        |
| Emma      | 1984                  | 4        |


## 2. LEFT JOIN

Returns all records from the left table (Customers), and matched records from Orders.

```SQL
SELECT Customers.FirstName, Orders.OrderID, Orders.Quantity
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```
| FirstName | OrderID | Quantity |
| --------- | ------- | -------- |
| John      | 1       | 1        |
| Jane      | 2       | 2        |
| Alice     | 3       | 1        |
| Michael   | 4       | 3        |
| Emily     | 5       | 2        |
| Chris     | 6       | 1        |
| Emma      | 7       | 4        |
| Daniel    | NULL    | NULL     |


## 3. RIGHT JOIN

Returns all records from the right table (Orders), and matched records from Customers.

```SQL
SELECT Customers.FirstName, Orders.OrderID, Orders.Quantity
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```
| FirstName | OrderID | Quantity |
| --------- | ------- | -------- |
| John      | 1       | 1        |
| Jane      | 2       | 2        |
| Alice     | 3       | 1        |
| Michael   | 4       | 3        |
| Emily     | 5       | 2        |
| Chris     | 6       | 1        |
| Emma      | 7       | 4        |


## 4. FULL OUTER JOIN

Returns all records when there is a match in either left or right table.

```SQL
SELECT Customers.FirstName, Orders.OrderID, Orders.Quantity
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```
| FirstName | OrderID | Quantity |
| --------- | ------- | -------- |
| John      | 1       | 1        |
| Jane      | 2       | 2        |
| Alice     | 3       | 1        |
| Michael   | 4       | 3        |
| Emily     | 5       | 2        |
| Chris     | 6       | 1        |
| Emma      | 7       | 4        |
| Daniel    | NULL    | NULL     |

## 5. SELF JOIN

A self join is a regular join but the table is joined with itself.

```SQL
SELECT A.FirstName AS Customer1, B.FirstName AS Customer2
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID;
```
| Customer1 | Customer2 |
| --------- | --------- |
| John      | Jane      |
| John      | Alice     |
| ...       | ...       |


## 6. UNION

Combines the result set of two or more SELECT statements.

```SQL
SELECT FirstName FROM Customers
UNION
SELECT Author FROM Books;
```
| FirstName           |
| ------------------- |
| John                |
| Jane                |
| Alice               |
| Michael             |
| Emily               |
| Chris               |
| Emma                |
| Daniel              |
| F. Scott Fitzgerald |
| Harper Lee          |
| George Orwell       |
| J.D. Salinger       |
| J.R.R. Tolkien      |
