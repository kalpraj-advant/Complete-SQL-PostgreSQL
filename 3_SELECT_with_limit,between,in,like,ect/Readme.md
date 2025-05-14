**Using `SELECT TOP`**:
   ```SQL
   SELECT TOP 3 * FROM Books
   ORDER BY PublishedYear ASC;
   ```
   | BookID | Title                  | Author              | Price | PublishedYear |
   | ------ | ---------------------- | ------------------- | ----- | ------------- |
   | 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |
   | 3      | 1984                   | George Orwell       | 8.99  | 1949          |
   | 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |


**Using `LIMIT`**:
   ```SQL
   SELECT * FROM Books
   LIMIT 3;
   ```
   | BookID | Title                  | Author              | Price | PublishedYear |
   | ------ | ---------------------- | ------------------- | ----- | ------------- |
   | 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
   | 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
   | 3      | 1984                   | George Orwell       | 8.99  | 1949          |

**Using `BETWEEN`**:
   ```SQL
   SELECT * FROM Books
   WHERE Price BETWEEN 8.00 AND 10.00;
   ```
   | BookID | Title                  | Author              | Price | PublishedYear |
   | ------ | ---------------------- | ------------------- | ----- | ------------- |
   | 3      | 1984                   | George Orwell       | 8.99  | 1949          |
   | 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |

**Using `IN`**:
   ```SQL
   SELECT * FROM Customers
   WHERE City IN ('New York', 'Chicago', 'Miami');
   ```
   | CustomerID | FirstName | LastName | Email            | City     |
   | ---------- | --------- | -------- | ---------------- | -------- |
   | 1          | John      | Doe      | john@example.com | New York |
   | 3          | Alice     | Brown    | alice@example.com| Chicago  |
   | 6          | Chris     | Wilson   | chris@example.com| Miami    |

**Using `LIKE`**:
   ```SQL
   SELECT * FROM Customers
   WHERE Email LIKE '%example.com';
   ```
   %abc - end 
   abc% - start
   %abc% - mid
   _a_b - 2-a, 4-b
   _a% - 2-a start
   
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

**Using `ILIKE`** (case-insensitive match):
   ```SQL
   SELECT * FROM Books
   WHERE Title ILIKE '%the%';
   ```
   | BookID | Title                  | Author              | Price | PublishedYear |
   | ------ | ---------------------- | ------------------- | ----- | ------------- |
   | 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
   | 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |