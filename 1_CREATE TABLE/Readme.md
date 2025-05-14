

#### Syntax:

```SQL
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...
);
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

SELECT * FROM Customers;
```

| CustomerID | FirstName | LastName | Email | City |
|------------|-----------|----------|-------|------|
|            |           |          |       |      |


#### Example:

```SQL
CREATE TABLE Books (
    BookID SERIAL PRIMARY KEY,
    Title VARCHAR(200),
    Author VARCHAR(150),
    Price DECIMAL(6, 2),
    PublishedYear INT
);

SELECT * FROM Books;
```

| BookID | Title | Author | Price | PublishedYear |
|--------|-------|--------|-------|---------------|
|        |       |        |       |               |


#### CREATE TABLE USING ANOTHER TABLE

#### Syntax:
```SQL
CREATE TABLE new_table_name AS
SELECT column1, column2, ...
FROM existing_table_name
WHERE ...;
```
#### Example:

```SQL
CREATE TABLE TestTable AS
SELECT CustomerID, Email
FROM Customers;
```
| CustomerID | Email |
|------------|--------|
|            |        |


### ADDING CONSTRAINTS IN CREATE TABLE

#### NOT NULL: column cannot have a NULL value.
##### Example:
```SQL
    ID INT NOT NULL,
    LastName VARCHAR(255) NOT NULL,
```
#### UNIQUE: all values in a column are unique.
##### Example:
```SQL
    Email VARCHAR(100) UNIQUE,
```
#### PRIMARY KEY: Uniquely identifies each record in a table.
##### Example:
```SQL
    ID INT PRIMARY KEY,
```
#### FOREIGN KEY: Links a column to another table’s primary key.
##### Example:
```SQL
    CustomerID INT REFERENCES Customers(CustomerID),
```
#### CHECK: Limits the range of values a column can accept.
##### Example:
```SQL
    Age INT CHECK (Age >= 18),
```
#### DEFAULT: Sets a default value for a column if no value is specified.
##### Example:
```SQL
    City VARCHAR(255) DEFAULT 'Sandnes',
    OrderDate DATE DEFAULT CURRENT_DATE,
```