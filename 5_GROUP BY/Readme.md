# GROUP BY

## Syntax

```SQL
SELECT column1, AGG_FUNC(column2)
FROM table_name
GROUP BY column1;
```

| category | data_value |
| -------- | ---------- |
| A        | 10         |
| A        | 5          |
| B        | 2          |
| B        | 4          |
| C        | 12         |
| C        | 6          |

```SQL
SELECT category, AVG(data_value) AS result
FROM data_table
GROUP BY category
ORDER BY category;
```

| category | result |
| -------- | ------ |
| A        | 7.5000 |
| B        | 3.0000 |
| C        | 9.0000 |


## Example: Orders

| OrderID | CustomerID | BookID | Quantity | OrderDate  |
| ------- | ---------- | ------ | -------- | ---------- |
| 1       | 1          | 2      | 1        | 2024-05-01 |
| 2       | 2          | 1      | 2        | 2024-05-03 |
| 3       | 3          | 3      | 1        | 2024-05-05 |
| 4       | 4          | 4      | 3        | 2024-05-06 |
| 5       | 5          | 5      | 2        | 2024-05-07 |
| 6       | 6          | 2      | 1        | 2024-05-08 |
| 7       | 7          | 3      | 4        | 2024-05-09 |


## Examples

### 1. Count Orders by Customer

```SQL
SELECT CustomerID, COUNT(*) AS TotalOrders
FROM Orders
GROUP BY CustomerID;
```
| CustomerID | TotalOrders |
| ---------- | ----------- |
| 1          | 1           |
| 2          | 1           |
| 3          | 1           |
| 4          | 1           |
| 5          | 1           |
| 6          | 1           |
| 7          | 1           |


### 2. Total Quantity Ordered by Book

```SQL
SELECT BookID, SUM(Quantity) AS TotalQuantity
FROM Orders
GROUP BY BookID;
```
| BookID | TotalQuantity |
| ------ | ------------- |
| 1      | 2             |
| 2      | 2             |
| 3      | 5             |
| 4      | 3             |
| 5      | 2             |


### 3. Average Quantity per Order Date

```SQL
SELECT OrderDate, AVG(Quantity) AS AvgQuantity
FROM Orders
GROUP BY OrderDate;
```
| OrderDate  | AvgQuantity |
| ---------- | ----------- |
| 2024-05-01 | 1.0         |
| 2024-05-03 | 2.0         |
| 2024-05-05 | 1.0         |
| 2024-05-06 | 3.0         |
| 2024-05-07 | 2.0         |
| 2024-05-08 | 1.0         |
| 2024-05-09 | 4.0         |


### 4. Using GROUP BY with HAVING

```SQL
SELECT BookID, SUM(Quantity) AS TotalQuantity
FROM Orders
GROUP BY BookID
HAVING SUM(Quantity) > 2;
```
| BookID | TotalQuantity |
| ------ | ------------- |
| 3      | 5             |
| 4      | 3             |

### 5. GROUP BY with WHERE

```SQL
SELECT BookID, SUM(Quantity) AS TotalQuantity
FROM Orders
WHERE Quantity > 1
GROUP BY BookID;
```
| BookID | TotalQuantity |
| ------ | ------------- |
| 1      | 2             |
| 3      | 4             |
| 4      | 3             |
| 5      | 2             |

---