## Syntax

```SQL
DELETE FROM table_name
WHERE condition;
```

## Example :

| CustomerID | FirstName | LastName | Email               | City        |
| ---------- | --------- | -------- | ------------------- | ----------- |
| 1          | John      | Doe      | john@example.com    | New York    |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles |
| 3          | Alice     | Brown    | alice@example.com   | Chicago     |


## 1. Delete a Specific Row

```SQL
DELETE FROM Customers
WHERE CustomerID = 3;
```

| CustomerID | FirstName | LastName | Email               | City        |
| ---------- | --------- | -------- | ------------------- | ----------- |
| 1          | John      | Doe      | john@example.com    | New York    |
| 2          | Jane      | Smith    | jane@example.com    | Los Angeles |
