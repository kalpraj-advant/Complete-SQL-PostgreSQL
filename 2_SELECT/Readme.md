

#### Syntax:

```SQL
SELECT column1, column2, ...
FROM table_name;

SELECT * FROM table_name;
```

#### Example:

```SQL
CREATE TABLE Customers (
    CustomerID SERIAL PRIMARY KEY,
    FirstName VARCHAR(100),
    LastName VARCHAR(100),
    Email VARCHAR(100),
    City VARCHAR(100)
);

CREATE TABLE Books (
    BookID SERIAL PRIMARY KEY,
    Title VARCHAR(200),
    Author VARCHAR(150),
    Price DECIMAL(6, 2),
    PublishedYear INT
);

CREATE TABLE Orders (
    OrderID SERIAL PRIMARY KEY,
    CustomerID INT REFERENCES Customers(CustomerID),
    BookID INT REFERENCES Books(BookID),
    Quantity INT,
    OrderDate DATE
);

-- Insert Data into Customers

INSERT INTO Customers (FirstName, LastName, Email, City)
VALUES 
('John', 'Doe', 'john@example.com', 'New York'),
('Jane', 'Smith', 'jane@example.com', 'Los Angeles'),
('Alice', 'Brown', 'alice@example.com', 'Chicago'),
('Michael', 'Johnson', 'michael@example.com', 'Houston'),
('Emily', 'Davis', 'emily@example.com', 'Phoenix'),
('Chris', 'Wilson', 'chris@example.com', 'Miami'),
('Emma', 'Garcia', 'emma@example.com', 'Seattle'),
('Daniel', 'Martinez', 'daniel@example.com', 'Denver');

-- Insert Data into Books

INSERT INTO Books (Title, Author, Price, PublishedYear)
VALUES 
('The Great Gatsby', 'F. Scott Fitzgerald', 10.99, 1925),
('To Kill a Mockingbird', 'Harper Lee', 7.99, 1960),
('1984', 'George Orwell', 8.99, 1949),
('The Catcher in the Rye', 'J.D. Salinger', 9.99, 1951),
('The Hobbit', 'J.R.R. Tolkien', 11.99, 1937);

-- Insert Data into Orders

INSERT INTO Orders (CustomerID, BookID, Quantity, OrderDate)
VALUES 
(1, 2, 1, '2024-05-01'),
(2, 1, 2, '2024-05-03'),
(3, 3, 1, '2024-05-05'),
(4, 4, 3, '2024-05-06'),
(5, 5, 2, '2024-05-07'),
(6, 2, 1, '2024-05-08'),
(7, 3, 4, '2024-05-09');

```
---
```SQL
    SELECT * FROM Customers;
```
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

---
```SQL
    SELECT * FROM Books;
```
| BookID | Title                  | Author              | Price | PublishedYear |
| ------ | ---------------------- | ------------------- | ----- | ------------- |
| 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
| 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
| 3      | 1984                   | George Orwell       | 8.99  | 1949          |
| 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |
| 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |

---
```SQL
    SELECT * FROM Orders;
```
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

### select with column name
```SQL
    SELECT Title, Price FROM Books;
```
| Title                  | Price |
| ---------------------- | ----- |
| The Great Gatsby       | 10.99 |
| To Kill a Mockingbird  | 7.99  |
| 1984                   | 8.99  |
| The Catcher in the Rye | 9.99  |
| The Hobbit             | 11.99 |

### Only Unique Rows Values form column
```SQL
    SELECT DISTINCT Quantity FROM Orders;
```
| Quantity |
| -------- |
| 1        |
| 2        |
| 3        |
| 4        |

## WHERE

#### Syntax:
```SQL
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

#### Examples:

**Using `=`**:
   ```SQL
   SELECT * FROM Customers
   WHERE City = 'New York';
   ```
   | CustomerID | FirstName | LastName | Email            | City     |
   | ---------- | --------- | -------- | ---------------- | -------- |
   | 1          | John      | Doe      | john@example.com | New York |

**Using `AND`**:
   ```SQL
   SELECT * FROM Books
   WHERE Price > 8.00 AND PublishedYear > 1950;
   ```
   | BookID | Title                  | Author              | Price | PublishedYear |
   | ------ | ---------------------- | ------------------- | ----- | ------------- |
   | 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |

**Using `OR`**:
   ```SQL
   SELECT * FROM Orders
   WHERE Quantity = 2 OR Quantity = 4;
   ```
   | OrderID | CustomerID | BookID | Quantity | OrderDate  |
   | ------- | ---------- | ------ | -------- | ---------- |
   | 2       | 2          | 1      | 2        | 2024-05-03 |
   | 7       | 7          | 3      | 4        | 2024-05-09 |

**Using `COUNT`**:
   ```SQL
   SELECT COUNT(*) AS TotalOrders
   FROM Orders
   WHERE Quantity > 1;
   ```
   | TotalOrders |
   | ----------- |
   | 4           |

**Using `ORDER BY`**:
   - **Ascending**:
     ```SQL
     SELECT * FROM Books
     ORDER BY Price ASC;
     ```
     | BookID | Title                  | Author              | Price | PublishedYear |
     | ------ | ---------------------- | ------------------- | ----- | ------------- |
     | 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
     | 3      | 1984                   | George Orwell       | 8.99  | 1949          |
     | 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |
     | 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
     | 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |

   - **Descending**:
     ```SQL
     SELECT * FROM Books
     ORDER BY Price DESC;
     ```
     | BookID | Title                  | Author              | Price | PublishedYear |
     | ------ | ---------------------- | ------------------- | ----- | ------------- |
     | 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |
     | 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
     | 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |
     | 3      | 1984                   | George Orwell       | 8.99  | 1949          |
     | 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
