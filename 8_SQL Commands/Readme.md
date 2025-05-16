# SQL Commands Reference

## 1. Timestamps and EXTRACT

**Timestamps** are used to store date and time information.  
The `EXTRACT` function retrieves specific parts (like year, month, day) from a date or timestamp.

```SQL
SELECT OrderDate, EXTRACT(YEAR FROM OrderDate) AS Year
FROM Orders;
```
| OrderDate  | Year |
| ---------- | ---- |
| 2024-05-01 | 2024 |
| 2024-05-03 | 2024 |


## 2. Math Functions

SQL provides several math functions for calculations.

- `ABS(x)` – Absolute value
- `ROUND(x, d)` – Round to d decimal places
- `CEIL(x)` – Smallest integer ≥ x
- `FLOOR(x)` – Largest integer ≤ x
- `POWER(x, y)` – x raised to the power y

```SQL
SELECT Price, ROUND(Price, 0) AS Rounded, POWER(Price, 2) AS Square
FROM Books;
```
| Price | Rounded | Square   |
| ----- | ------- | -------- |
| 10.99 | 11      | 120.7801 |
| 7.99  | 8       | 63.8401  |

- `ABS(x)` – Absolute value  
  ```SQL
  SELECT -5 AS Number, ABS(-5) AS AbsoluteValue;
  ```
  | Number | AbsoluteValue |
  | ------ | ------------- |
  | -5     | 5             |

- `ROUND(x, d)` – Round to d decimal places  
  ```SQL
  SELECT 10.678 AS Number, ROUND(10.678, 1) AS Rounded;
  ```
  | Number | Rounded |
  | ------ | ------- |
  | 10.678 | 10.7    |

- `CEIL(x)` – Smallest integer ≥ x  
  ```SQL
  SELECT 7.2 AS Number, CEIL(7.2) AS CeilValue;
  ```
  | Number | CeilValue |
  | ------ | --------- |
  | 7.2    | 8         |

- `FLOOR(x)` – Largest integer ≤ x  
  ```SQL
  SELECT 7.8 AS Number, FLOOR(7.8) AS FloorValue;
  ```
  | Number | FloorValue |
  | ------ | ---------- |
  | 7.8    | 7          |

- `POWER(x, y)` – x raised to the power y  
  ```SQL
  SELECT 3 AS Base, 2 AS Exponent, POWER(3, 2) AS Result;
  ```
  | Base | Exponent | Result |
  | ---- | -------- | ------ |
  | 3    | 2        | 9      |


## 3. String Functions

String functions help manipulate text data.

- `UPPER(str)` – Convert to uppercase
- `LOWER(str)` – Convert to lowercase
- `LENGTH(str)` – Length of string
- `SUBSTRING(str, start, length)` – Extract part of string
- `CONCAT(str1, str2)` – Concatenate strings

```SQL
SELECT FirstName, UPPER(FirstName) AS UpperName, LENGTH(FirstName) AS NameLength
FROM Customers;
```
| FirstName | UpperName | NameLength |
| --------- | --------- | ---------- |
| John      | JOHN      | 4          |
| Jane      | JANE      | 4          |

- `UPPER(str)` – Convert to uppercase  
  ```SQL
  SELECT 'hello' AS Original, UPPER('hello') AS Uppercase;
  ```
  | Original | Uppercase |
  | -------- | --------- |
  | hello    | HELLO     |

- `LOWER(str)` – Convert to lowercase  
  ```SQL
  SELECT 'WORLD' AS Original, LOWER('WORLD') AS Lowercase;
  ```
  | Original | Lowercase |
  | -------- | --------- |
  | WORLD    | world     |

- `LENGTH(str)` – Length of string  
  ```SQL
  SELECT 'SQL' AS Text, LENGTH('SQL') AS Length;
  ```
  | Text | Length |
  | ---- | ------ |
  | SQL  | 3      |

- `SUBSTRING(str, start, length)` – Extract part of string  
  ```SQL
  SELECT 'Database' AS Word, SUBSTRING('Database', 1, 4) AS SubStr;
  ```
  | Word     | SubStr |
  | -------- | ------ |
  | Database | Data   |

- `CONCAT(str1, str2)` – Concatenate strings  
  ```SQL
  SELECT 'Data' AS Part1, 'Base' AS Part2, CONCAT('Data', 'Base') AS Combined;
  ```
  | Part1 | Part2 | Combined |
  | ----- | ----- | -------- |
  | Data  | Base  | DataBase |

## 4. Sub-query

A **sub-query** is a query nested inside another query.

```SQL
SELECT Title, Price
FROM Books
WHERE Price > (SELECT AVG(Price) FROM Books);
```
| Title            | Price |
| ---------------- | ----- |
| The Great Gatsby | 10.99 |
| The Hobbit       | 11.99 |
