
## (Q1) Créer la base donnée sous nom "boutique".
```sql
    CREATE DATABESE boutique
```
__________________________________________________________________________________________
## (Q2) Création des tables (Manufacturers, Products).
```sql
    CREATE TABLE Manufacturers(
    Code INT auto_increment,
    Name varchar(100),
    primary key(Code)
    );
    CREATE TABLE Products(
    Code INT auto_increment,
    Name VARCHAR(100),
    Price float,
    Manufacturer_code INT,
    primary key(Code),
    foreign key(Manufacturer_code) references manufacturers(Code)
    );
```
__________________________________________________________________________________________
## (Q3) Insérer dans le tableau Manufacturers les valeurs :
```sql
    INSERT INTO manufacturers (Name) VALUES ('Sony'), ('Creative Labs'), ('Hewlett-Packard'), ('Iomega'), ('Fujitsu'), ('Winchester');
```
__________________________________________________________________________________________
## (Q4) Insérer dans le tableau Products : 

```sql
    INSERT INTO products (Name, Price, Manufacturer_code) VALUES 
('Hard drive', 240.00, 5),
('Memory', 120.00, 6),
('ZIP drive', 150.00, 4),
('Floppy disk', 5.00, 6),
('Monitor', 240.00, 1),
('DVD drive', 180.00, 2),
('CD drive', 90.00, 2),
('Printer', 270.00, 3),
('Toner cartridge', 66.00, 3),
('DVD burner', 180.00, 2) ;
```
__________________________________________________________________________________________
## (Q5) Sélectionnez les noms de tous les produits du magasin.
```sql
    SELECT Name FROM products;
```
__________________________________________________________________________________________
## (Q6) Sélectionner les noms et les prix de tous les produits du magasin.
```sql
    SELECT Name, Price FROM products;
```
__________________________________________________________________________________________
## (Q7) Sélectionner le nom des produits dont le prix est inférieur ou égal à 200 $.
```sql
    SELECT Name FROM products WHERE Price <= 200;
```
__________________________________________________________________________________________
## (Q8) Sélectionnez tous les produits dont le prix est compris entre 60 et 120 dollars.
```sql
    SELECT * FROM products WHERE Price between 60 and 120;
```
__________________________________________________________________________________________
## (Q9) Sélectionnez le nom et le prix en cents (c'est-à-dire que le prix doit être multiplié par 100).
```sql
    SELECT Price*100  AS Price_Cents, Name FROM products ;
```
__________________________________________________________________________________________
## (Q10) Calculer le prix moyen de tous les produits.
```sql
    SELECT AVG(Price) FROM products ;
```
__________________________________________________________________________________________
## (Q11) Calculer le prix moyen de tous les produits dont le code fabricant est égal à 2.
```sql
    SELECT AVG(Price) FROM products WHERE Manufacturer_code = 2 ;
```
__________________________________________________________________________________________
## (Q12) Calculer le nombre de produits dont le prix est supérieur ou égal à 180 dollars.
```sql
    SELECT count(*) FROM products WHERE price >= 180 ;
```
__________________________________________________________________________________________
## (Q13) Sélectionner le nom et le prix de tous les produits dont le prix est supérieur ou égal à 180 dollars, et trier d'abord par prix (par ordre décroissant), puis par nom (par ordre croissant).
```sql
    SELECT Name, Price FROM products WHERE price >= 180 order by Price desc,Name Asc;
```
__________________________________________________________________________________________
## (Q14) Sélectionnez toutes les données des produits, y compris toutes les données relatives au fabricant de chaque produit.
```sql
    SELECT * FROM products INNER JOIN manufacturers on products.Manufacturer_code = manufacturers.Code;
```
__________________________________________________________________________________________
## (Q15) Sélectionnez le nom du produit, le prix et le nom du fabricant de tous les produits.
```sql
    SELECT products.Name, products.Price, manufacturers.Name FROM products INNER JOIN manufacturers on products.Manufacturer_code = manufacturers.Code;
```
__________________________________________________________________________________________
## (Q16) Sélectionnez le prix moyen des produits de chaque fabricant, en indiquant uniquement le code du fabricant.
```sql
    SELECT  AVG(Price), Manufacturer_code FROM products group by Manufacturer_code;
```
__________________________________________________________________________________________
## (Q17) Sélectionnez le prix moyen des produits de chaque fabricant, en indiquant le nom du fabricant.
```sql
    SELECT  AVG(Price), manufacturers.Name FROM products INNER JOIN manufacturers on products.Manufacturer_code = manufacturers.Code group by Manufacturer_code;
```
__________________________________________________________________________________________
## (Q18) Sélectionnez les noms des fabricants dont les produits ont un prix moyen supérieur ou égal à 150 $.
```sql
    SELECT  AVG(Price), manufacturers.Name FROM products INNER JOIN manufacturers on products.Manufacturer_code = manufacturers.Code group by Manufacturer_code  having AVG(Price) >= 150;
```
__________________________________________________________________________________________
## (Q19) Sélectionnez le nom et le prix du produit le moins cher.
```sql
    SELECT Name, Price FROM products WHERE Price = (SELECT min(Price) FROM products);
```
__________________________________________________________________________________________
## (Q20) Sélectionnez le nom de chaque fabricant ainsi que le nom et le prix de son produit le plus cher.
```sql
    SELECT M.name, P.Name, P.Price FROM products P join manufacturers M on P.Manufacturer_code = M.Code group by Manufacturer_code ;
```
__________________________________________________________________________________________
## (Q21) Ajouter un nouveau produit : Loudspeakers, 70 $, manufacter 2 
```sql
    INSERT INTO products (Name, Price, Manufacturer_code) VALUES ('Loudspeakers', 70.00, 2);
```
__________________________________________________________________________________________
## (Q22) Mettre à jour le nom du produit 8 en "laser Print".
```sql
    UPDATE products SET Name = 'Laser Print' WHERE Code = 8;
```
__________________________________________________________________________________________
## (Q23) Appliquer une remise de 10 % à tous les produits.
```sql
    UPDATE products SET Price = Price*0.9;
    UPDATE products SET Price = Price - (Price*0.1);
```
__________________________________________________________________________________________
## (Q24) Appliquer une remise de 10 % à tous les produits dont le prix est supérieur ou égal à 120 $.
```sql
    UPDATE products SET Price = Price*0.9 WHERE Price >= 120;
```