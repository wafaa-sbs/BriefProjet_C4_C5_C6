## 1 Sélectionnez le nom de famille de tous les employés.
```sql
    SELECT LastName FROM employees
```
__________________________________________________________________________________________
## 2 Sélectionnez le nom de famille de tous les employés, sans doublons.
```sql
    SELECT DISTINCT LastName FROM employees
```
__________________________________________________________________________________________
## 3 Sélectionnez toutes les données des employés dont le nom de famille est "Smith".
```sql
    SELECT * FROM employees  WHERE LastName= 'Smith'
```
__________________________________________________________________________________________
## 4 Sélectionnez toutes les données des employés dont le nom de famille est "Smith" ou "Doe".
```sql
   SELECT * FROM employees WHERE 'smith' or 'doe'
```
__________________________________________________________________________________________
## .5 Sélectionnez toutes les données des employés qui travaillent dans le département 14.
```sql
    SELECT * FROM employees WHERE Department= 14
```
__________________________________________________________________________________________
## 6 Sélectionner toutes les données des employés qui travaillent dans le département 37 ou le département 77.
```sql
    SELECT * FROM employees WHERE Department= 37 OR Department= 77
```
__________________________________________________________________________________________
## 7 Sélectionner toutes les données des employés dont le nom de famille commence par un "S".
```sql
    SELECT * FROM employees WHERE LastName like 's%'
```
__________________________________________________________________________________________
## 8 Sélectionner la somme des budgets de tous les départements.
```sql
    SELECT SUM(Budget) FROM departments
```
__________________________________________________________________________________________
## 9 Sélectionnez le nombre d'employés dans chaque département (vous devez seulement indiquer le code du département et le nombre d'employés).
```sql
    SELECT COUNT(*) AS conteur,Department AS code 
    FROM employees GROUP BY Department
```
__________________________________________________________________________________________
## 10 Sélectionnez toutes les données des employés, y compris les données du département de chaque employé.
```sql
    SELECT p.Name AS employee,d.Name AS departement 
    FROM employees p INNER JOIN departments d ON p.Department=d.Code;
```
__________________________________________________________________________________________
## 11 Sélectionnez le nom et le prénom de chaque employé, ainsi que le nom et le budget du département de l'employé.
```sql
    SELECT e.Name, e.LastName, d.Name, d.budget 
    FROM employees e INNER JOIN departments d ON e.Department = d.code
```
__________________________________________________________________________________________
## 12 Sélectionnez le nom et le nom de famille des employés travaillant pour des ministères dont le budget est supérieur à 60 000 $.
```sql
    SELECT e.Name, e.LastName, d.Name, d.budget 
    FROM employees e INNER JOIN departments d ON e.Department = d.code
    WHERE budget>60000
```
__________________________________________________________________________________________
## 13 Sélectionnez les départements dont le budget est supérieur au budget moyen de l'ensemble des départements.
```sql
    SELECT *
    from Departments
    WHERE budget>(SELECT AVG(budget)FROM Departments)
```
__________________________________________________________________________________________
## 14 Sélectionnez les noms des départements ayant plus de deux employés.
```sql 
    SELECT d.Name 
    FROM departments d INNER JOIN employees e ON e.Department=d.code
    GROUP BY d.Name HAVING COUNT(*) >2;
```
__________________________________________________________________________________________
## 15 Sélectionnez le nom et le nom de famille des employés travaillant pour les ministères dont le budget est le deuxième plus bas.
```sql
    SELECT e.Name, e.LastName, d.Budget 
    FROM Employees e INNER JOIN departments d ON e.Department = d.code WHERE e.Department = (SELECT sub.Code 
    FROM (SELECT * FROM Departments d ORDER BY d.budget desc LIMIT 2) sub ORDER BY budget DESC LIMIT 1)
```
__________________________________________________________________________________________
## 16 Ajoutez un nouveau service appelé "Quality assurance", avec un budget de 40 000 $ et le code de service 11. Et ajoutez un employé appelé "Mary Moore" dans ce département, avec le code SSN 847-21-9811.
```sql
    insert into departments values(11, 'Quality Assurance', 40000);
    insert into employees values(847219811, 'Mary', 'Moore', 11);
```
__________________________________________________________________________________________
## 17 Réduire le budget de tous les départements de 10 %.
```sql
    update departments set budget = 0.9 * budget;
```
__________________________________________________________________________________________
## 18 Réaffecter tous les employés du département de la recherche (code 77) au département informatique (code 14)
```sql
    UPDATE employees SET Department = 14 WHERE Department = 7
```
__________________________________________________________________________________________
## 19 Supprimer du tableau tous les employés du département informatique (code 14).
```sql 
    delete from employees where department = 14;
```
__________________________________________________________________________________________
## 20 Supprimer du tableau tous les employés qui travaillent dans des départements dont le budget est supérieur ou égal à 60 000 $.
```sql 
    DELETE from employees WHERE Department in (SELECT Code FROM departments WHERE budget > 60000)
```
__________________________________________________________________________________________
## 21  Supprimer du tableau tous les employées
```sql
     delete from employees;
```