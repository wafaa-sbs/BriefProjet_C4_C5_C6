## Question 1
```sql
SELECT Title  FROM Movies; 
```
__________________________________________________________________________________________
## question 2
```sql
. SELECT DISTINCT Rating  FROM Movies; 
```
__________________________________________________________________________________________
## question 3
```sql
. SELECT *  FROM Movies  WHERE Rating IS NULL; 
```
__________________________________________________________________________________________
## question 4
```sql 
. SELECT *  FROM MovieTheaters  WHERE Movie IS NULL; 
```
__________________________________________________________________________________________
## question 5
```sql 
. SELECT * FROM MovieTheaters LEFT JOIN Movies ON MovieTheaters.Movie = Movies.Code; 
```
__________________________________________________________________________________________
## question 6 
```sql
SELECT * FROM MovieTheaters RIGHT JOIN Movies ON MovieTheaters.Movie = Movies.Code; 
```
__________________________________________________________________________________________
## question 7 
```sql
. SELECT Title FROM Movies 
 WHERE Code NOT IN 
   ( 
     SELECT Movie FROM MovieTheaters 
     WHERE Movie IS NOT NULL 
   ); 
```
__________________________________________________________________________________________
## question 8
```sql
. INSERT INTO Movies(Title,Rating) VALUES('One, Two, Three',NULL);
``` 
__________________________________________________________________________________________
## question 9
```sql
. UPDATE Movies SET Rating='G' WHERE Rating IS NULL; 
10/ 
. DELETE FROM MovieTheaters WHERE Movie IN 
   (SELECT Code FROM Movies WHERE Rating = 'NC-17'); 
```