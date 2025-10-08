# Experiment 2: DDL Commands

### Name : Lahari sindhu.G
### Register Number : 212223240038

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
Insert all books from Out_of_print_books into Books

Table attributes are ISBN, Title, Author, Publisher, YearPublished

```sql
INSERT INTO Books
(ISBN,Title,Author,publisher,YearPublished)                                                                                                                                                                                                                                                 
SELECT ISBN,Title,Author,publisher,YearPublished
FROM Out_of_print_books;

```

**Output:**
![WhatsApp Image 2025-10-08 at 05 56 30_aa1beed3](https://github.com/user-attachments/assets/62384ae1-1e54-46c9-bcac-b80112cae4ca)




**Question 2**
---
Create a table named Orders with the following columns:

OrderID as INTEGER
OrderDate as TEXT
CustomerID as INTEGER

```sql
CREATE TABLE Orders (
     OrderID INTEGER,
     OrderDate TEXT,
     CustomerID INTEGER
);


```

**Output:**

![WhatsApp Image 2025-10-08 at 05 57 49_ce4c8616](https://github.com/user-attachments/assets/00334e88-4979-4be9-ac78-0ae02ff59e1f)




**Question 3**
---
Create a new table named products with the following specifications:
product_id as INTEGER and primary key.
product_name as TEXT and not NULL.
list_price as DECIMAL (10, 2) and not NULL.
discount as DECIMAL (10, 2) with a default value of 0 and not NULL.
A CHECK constraint at the table level to ensure:
list_price is greater than or equal to discount
discount is greater than or equal to 0
list_price is greater than or equal to 0

```sql
CREATE TABLE products(
  product_id INTEGER PRIMARY KEY,
  product_name TEXT NOT NULL,
  list_price DECIMAL(10,2) NOT NULL,
  discount DECIMAL(10,2) NOT NULL DEFAULT 0,
  CHECK (list_price>=discount AND discount>=0 AND list_price>=0)
);
  
```

**Output:**
![WhatsApp Image 2025-10-08 at 05 58 57_d0f1e384](https://github.com/user-attachments/assets/b4c1252c-1e5a-4c85-b53d-a5d167d6c7ec)



**Question 4**
---
Write a SQL query to Add a new column mobilenumber as number in the Student_details table.

Sample table: Student_details

 cid              name             type   notnull     dflt_value  pk
---------------  ---------------  -----  ----------  ----------  ----------
0                RollNo           int    0                       1
1                Name             VARCH  1                       0
2                Gender           TEXT   1                       0
3                Subject          VARCH  0                       0
4                MARKS            INT (  0                       0
```sql
ALTER TABLE Student_details
ADD COLUMN mobilenumber number;
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 00 12_6eba034d](https://github.com/user-attachments/assets/f716593a-f8a0-4c8f-8f8a-a5ce220d26dd)



**Question 5**
---
Create a table named Invoices with the following constraints:
InvoiceID as INTEGER should be the primary key.
InvoiceDate as DATE.
Amount as REAL should be greater than 0.
DueDate as DATE should be greater than the InvoiceDate.
OrderID as INTEGER should be a foreign key referencing Orders(OrderID).

```sql
CREATE TABLE Invoices(
   InvoiceID INTEGER PRIMARY KEY,
   InvoiceDate DATE,
   Amount REAL CHECK(Amount > 0),
   DueDate DATE CHECK(DueDate > InvoiceDate),
   OrderID INTEGER,
   FOREIGN KEY (orderID) REFERENCES Orders(OrderID)
);
```

**Output:**
![Uploading WhatsApp Image 2025-10-08 at 06.01.09_5b9519ba.jpg…]()



**Question 6**
---
Create a new table named contacts with the following specifications:
contact_id as INTEGER and primary key.
first_name as TEXT and not NULL.
last_name as TEXT and not NULL.
email as TEXT.
phone as TEXT and not NULL with a check constraint to ensure the length of phone is at least 10 characters.

```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name TEXT NOT NULL,
    last_name TEXT NOT NULL,
    email TEXT,
    phone TEXT NOT NULL CHECK (LENGTH(phone)>=10)
);
```

**Output:**

![Uploading WhatsApp Image 2025-10-08 at 06.02.10_8db9f56c.jpg…]()



**Question 7**
---
Insert a record with EmployeeID 001, Name Sarah Parker, Position Manager, Department HR, and Salary 60000 into the Employee table.

```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (001,'Sarah Parker','Manager','HR',60000);
```

**Output:**

![WhatsApp Image 2025-10-08 at 06 03 43_0385919f](https://github.com/user-attachments/assets/f1c41c89-f966-4d08-b7ac-a1ccdc66a807)



**Question 8**
---
Create a table named Tasks with the following columns:
TaskID as INTEGER
TaskName as TEXT
DueDate as DATE

```sql
CREATE TABLE Tasks(
TaskID INTEGER,
TaskName TEXT,
DueDate DATE
);
```

**Output:**

![image](https://github.com/user-attachments/assets/9f9a0a4e-5d8a-4663-98ae-536cf84a0baf)


**Question 9**
---
Insert the following employees into the Employee table:

EmployeeID  Name        Position    Department  Salary
----------  ----------  ----------  ----------  ----------
2           John Smith  Developer   IT          75000
3           Anna Bell   Designer    Marketing   68000
```sql
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (002,'John Smith','Developer','IT',75000);
INSERT INTO Employee(EmployeeID,Name,Position,Department,Salary)
VALUES (003,'Anna Bell','Designer','Marketing',68000);
```

**Output:**
![WhatsApp Image 2025-10-08 at 06 05 03_73a0acc2](https://github.com/user-attachments/assets/0e964c8d-77b0-428e-8f1f-e1f4f439f54b)



**Question 10**
---
Write an SQL Query to add the attributes designation, net_salary, and dob to the Companies table with the following data types:
designation as VARCHAR(50)
net_salary as NUMBER
dob as DATE

```sql
ALTER TABLE Companies 
ADD COLUMN designation varchar(50);
ALTER TABLE Companies 
ADD COLUMN net_salary number;
ALTER TABLE Companies 
ADD COLUMN dob date;
```

**Output:**

![image](https://github.com/user-attachments/assets/0c063267-1d3c-486d-9b6a-4770063e4b2c)



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
