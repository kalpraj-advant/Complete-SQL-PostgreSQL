# Aggregate Functions

Most Common Aggregate Functions:  
- **AVG()** - returns average value  
- **COUNT()** - returns number of values  
- **MAX()** - returns maximum value  
- **MIN()** - returns minimum value  
- **SUM()** - returns the sum of all values  
- **VARIANCE()** - returns the statistical variance  
- **STDDEV()** - returns the standard deviation  


---

## Examples
`Books` table:

| BookID | Title                  | Author              | Price | PublishedYear |
| ------ | ---------------------- | ------------------- | ----- | ------------- |
| 1      | The Great Gatsby       | F. Scott Fitzgerald | 10.99 | 1925          |
| 2      | To Kill a Mockingbird  | Harper Lee          | 7.99  | 1960          |
| 3      | 1984                   | George Orwell       | 8.99  | 1949          |
| 4      | The Catcher in the Rye | J.D. Salinger       | 9.99  | 1951          |
| 5      | The Hobbit             | J.R.R. Tolkien      | 11.99 | 1937          |

---

### AVG()

```SQL
SELECT AVG(Price) AS AveragePrice FROM Books;
```
| AveragePrice |
| ------------ |
| 9.99         |

---

### COUNT()

```SQL
SELECT COUNT(*) AS TotalBooks FROM Books;
```
| TotalBooks |
| ---------- |
| 5          |

---

### MAX()

```SQL
SELECT MAX(Price) AS MaxPrice FROM Books;
```
| MaxPrice |
| -------- |
| 11.99    |

---

### MIN()

```SQL
SELECT MIN(Price) AS MinPrice FROM Books;
```
| MinPrice |
| -------- |
| 7.99     |

---

### SUM()

```SQL
SELECT SUM(Price) AS TotalPrice FROM Books;
```
| TotalPrice |
| ---------- |
| 49.95      |

---

### VARIANCE()

```SQL
SELECT VARIANCE(Price) AS PriceVariance FROM Books;
```
| PriceVariance |
| ------------- |
| 2.50          |

---

### STDDEV()

```SQL
SELECT STDDEV(Price) AS PriceStdDev FROM Books;
```
| PriceStdDev |
| ----------- |
| 1.58        |