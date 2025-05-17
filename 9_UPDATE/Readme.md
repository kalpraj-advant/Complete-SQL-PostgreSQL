
## Syntax

```SQL
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```


## Example :

| CustomerID | FirstName | LastName | Email               | City        |
| ---------- | --------- | -------- | ------------------- | ----------- |
| 1          | John      | Doe      | john@example.com    | New York    |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles |
| 3          | Alice     | Brown    | alice@example.com   | Chicago     |

## 1. Update a Single Column

```SQL
UPDATE Customers
SET City = 'Boston'
WHERE CustomerID = 3;
```

| CustomerID | FirstName | LastName | Email               | City        |
| ---------- | --------- | -------- | ------------------- | ----------- |
| 1          | John      | Doe      | john@example.com    | New York    |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles |
| 3          | Alice     | Brown    | alice@example.com   | Boston      |


## 2. Update Multiple Columns

```SQL
UPDATE Customers
SET FirstName = 'Alicia', City = 'San Francisco'
WHERE CustomerID = 3;
```

| CustomerID | FirstName | LastName | Email               | City          |
| ---------- | --------- | -------- | ------------------- | ------------- |
| 1          | John      | Doe      | john@example.com    | New York      |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles   |
| 3          | Alicia    | Brown    | alice@example.com   | San Francisco |


## 3. Update All Rows (Use with Caution)

```SQL
UPDATE Customers
SET City = 'USA';
```

| CustomerID | FirstName | LastName | Email               | City |
| ---------- | --------- | -------- | ------------------- | ---- |
| 1          | John      | Doe      | john@example.com    | USA  |
| 2          | Jane      | Smith    | jane@example.com    | USA  |
| 3          | Alicia    | Brown    | alice@example.com   | USA  |


## 4. Update Using Another Table

```SQL
UPDATE Customers
SET City = Orders.OrderCity
FROM Orders
WHERE Customers.CustomerID = Orders.CustomerID;
```