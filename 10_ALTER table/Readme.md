## 1. Add a Column

```SQL
ALTER TABLE Customers
ADD Age INT;
```

## 2. Drop a Column

```SQL
ALTER TABLE Customers
DROP COLUMN Age;
```

## 3. Rename a Column

```SQL
ALTER TABLE Customers
RENAME COLUMN FirstName TO GivenName;
```

## 4. Change a Column's Data Type

```SQL
ALTER TABLE Customers
ALTER COLUMN City TYPE VARCHAR(200);
```

```SQL
ALTER TABLE Customers
ALTER COLUMN City SET/DROP NOT NULL;
```

## 5. Set DEFAULT Value for a Column

```SQL
ALTER TABLE Customers
ALTER COLUMN City SET DEFAULT 'Unknown';
```

## 6. Add a CHECK Constraint

```SQL
ALTER TABLE Customers
ADD CONSTRAINT chk_age CHECK (Age >= 0);
```

## 7. Rename the Table

```SQL
ALTER TABLE Customers
RENAME TO Clients;
```