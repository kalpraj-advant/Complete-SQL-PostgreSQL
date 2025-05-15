### 1. How many payment transactions were greater than $5.00?
```SQL
SELECT COUNT(amount) FROM payment
WHERE amount > 5;
```
### 2. How many actors have a first name that starts with the letter P?
```SQL
SELECT COUNT(*) FROM actor WHERE first_name LIKE 'P%';
```
### 3. How many unique districts are our customers from?
```SQL
SELECT COUNT(DISTINCT(district)) FROM address;
```
### 4. print unique districts
```SQL
SELECT DISTINCT(district) FROM address;
```
### 5. How many films have a rating of R and a replacement cost between $5 and $15?
```SQL
SELECT COUNT(*) FROM film
WHERE rating = 'R'
AND replacement_cost BETWEEN 5 AND 15;
```
### 6. How many films have the word Truman somewhere in the title?
```SQL
SELECT COUNT(*) FROM film WHERE title LIKE '%Truman%';
```