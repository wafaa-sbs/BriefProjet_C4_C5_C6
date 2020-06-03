## question 1
```sql
. SELECT   S.Name, P.Name, P.Hours 
FROM     Scientists S  
         INNER JOIN AssignedTo A ON S.SSN=A.Scientist 
         INNER JOIN Projects P ON A.Project=P.Code 
ORDER BY P.Name ASC, S.Name ASC; 
```
__________________________________________________________________________________________
## question 2
```sql
. SELECT projects.Name  FROM projects  
RIGHT JOIN assignedto ON projects.Code = assignedto.Project 
```