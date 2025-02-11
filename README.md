# Huda's Project -Adv Coding


## Create codes for 10 queries 💻


#### 1. Display All Cinemas with a Rating of 5
```sql
SELECT * FROM ksa WHERE rating = 5;
```
<img width="1405" alt="1" src="https://github.com/user-attachments/assets/12b5c81d-4b0b-437c-b7e0-675da9b96bd2" />

#### 2. Count the Number of Cinemas by Genre

```sql
SELECT genre, COUNT(*) AS cinema_count FROM ksa GROUP BY genre;
```

<img width="1405" alt="2" src="https://github.com/user-attachments/assets/5904db6b-1aa7-40a3-9c28-1c80df34ffb6" />

#### 3. Find Cinemas with More Than 50,000 Reviews

```sql
SELECT * FROM ksa WHERE review_count > 50000;
```

<img width="1405" alt="3" src="https://github.com/user-attachments/assets/9c4afcbf-59f2-4599-bcf3-f705843deefd" />

#### 4. Calculate Average Rating for Each Genre

```sql
SELECT genre, AVG(rating) AS average_rating FROM ksa GROUP BY genre;
```

<img width="1405" alt="4" src="https://github.com/user-attachments/assets/598fea8f-46b1-4d74-8d19-fcdf7967c33b" />

#### 5. List Cinemas Without Any Best Comment

```sql
SELECT * FROM ksa WHERE best_comment IS NULL;
```

<img width="1405" alt="5" src="https://github.com/user-attachments/assets/7099a341-0189-45d7-8730-503031581fa4" />

#### 6. Top 5 Cinemas with the Highest Number of Reviews

```sql
SELECT * FROM ksa ORDER BY review_count DESC LIMIT 5;
```
<img width="1405" alt="6" src="https://github.com/user-attachments/assets/bcc47a8e-ae03-4211-82af-44addf8c79ba" />

#### 7. Find Cinemas Located in Saudi Arabia

```sql
SELECT * FROM ksa WHERE location LIKE '%Saudi Arabia%';
```
<img width="1405" alt="7" src="https://github.com/user-attachments/assets/c57810c0-be4f-4088-9fed-a78ade653773" />

#### 8. Update Ratings of 0 to 3

```sql
UPDATE ksa SET rating = 3 WHERE rating = 0;
```

<img width="1405" alt="8:1" src="https://github.com/user-attachments/assets/5642557a-de0d-4dd9-bd37-ebadcaaac85b" />

##### check if it is work 
``` sql
SELECT * FROM ksa WHERE rating = 3;
```

<img width="1405" alt="8:2" src="https://github.com/user-attachments/assets/168fa543-13db-42d5-810f-01379018d004" />

#### 9. Delete Cinemas with Zero Reviews
```sql
DELETE FROM ksa WHERE review_count = 0;
```

<img width="1405" alt="9:1" src="https://github.com/user-attachments/assets/acf1c194-dc62-4431-a407-8301fe80316f" />

##### check if it is work 

``` sql
SELECT * FROM ksa WHERE review_count = 0;
```

<img width="1405" alt="9:2" src="https://github.com/user-attachments/assets/777974fa-7dc0-4793-ad90-0562f8521707" />




#### 10. Find Cinemas with Comments Mentioning 'Perfect'

```sql
SELECT * FROM ksa WHERE best_comment LIKE '%perfect%';
```

<img width="1405" alt="10" src="https://github.com/user-attachments/assets/25ffd67d-3c38-462b-87bd-dda956b6c7dd" />


# 🎯 Bonus Section

#### 1. Trigger to Automatically Set Rating to 1 If Inserted as 0
``` sql
DELIMITER //
CREATE TRIGGER set_default_rating
BEFORE INSERT ON ksa
FOR EACH ROW
BEGIN
    IF NEW.rating = 0 THEN
        SET NEW.rating = 1;
    END IF;
END;
//
DELIMITER ;

```
<img width="781" alt="Screenshot 1446-08-12 at 1 24 16 PM" src="https://github.com/user-attachments/assets/4708aa42-2e95-4bec-96fd-85d098a4b8ee" />

##### check if it is work 

``` sql
SELECT * FROM ksa WHERE rating = 1;
```
<img width="1405" alt="Screenshot 1446-08-12 at 1 29 03 PM" src="https://github.com/user-attachments/assets/f25e341a-dba9-471c-be65-1ede3a35152b" />


#### 2. Function to Calculate Average Rating by Genre

```
sql
DELIMITER $$

CREATE FUNCTION get_average_rating(genre_name VARCHAR(255))
RETURNS DECIMAL(5,2)
DETERMINISTIC
BEGIN
    DECLARE avg_rating DECIMAL(5,2);
    
    SELECT AVG(COALESCE(rating, 0)) INTO avg_rating
    FROM ksa
    WHERE genre = genre_name;
    
    RETURN avg_rating;
END$$

DELIMITER ;

```
<img width="1405" alt="Screenshot 1446-08-12 at 1 36 24 PM" src="https://github.com/user-attachments/assets/86dde401-d836-48b0-9beb-d985391c45d6" />




##### check if it is work 

``` sql
SELECT get_average_rating('Movie Theater') AS average_rating;
```
<img width="1405" alt="Screenshot 1446-08-12 at 1 37 27 PM" src="https://github.com/user-attachments/assets/1ccbe7ac-cdd3-4478-85ee-ab2b3a6062fb" />


# DONE ✅














