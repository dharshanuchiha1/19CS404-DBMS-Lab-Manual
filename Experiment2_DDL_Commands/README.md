# Experiment 2: DDL Commands

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
<img width="1242" height="442" alt="Screenshot 2026-08-07 113117" src="https://github.com/user-attachments/assets/def8a6f2-033a-459a-858b-f36b26c232b9" />


```sql
CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10,2) NOT NULL,
    discount DECIMAL(10,2) NOT NULL DEFAULT 0,
    CHECK (
        list_price >= discount
        AND discount >= 0
        AND list_price >= 0
    )
);
```

**Output:**

<img width="1072" height="180" alt="Screenshot 2026-08-07 113207" src="https://github.com/user-attachments/assets/f9a73e40-e2d7-4bed-a6cb-9aaf6dada865" />


**Question 2**
---
<img width="1287" height="317" alt="Screenshot 2026-08-07 113236" src="https://github.com/user-attachments/assets/231ed8d6-8d0c-4a24-84e0-a0c94fbbcd72" />


```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1157" height="292" alt="Screenshot 2026-08-07 113310" src="https://github.com/user-attachments/assets/32337b4d-f564-4039-8f3c-45af1efd7edf" />


**Question 3**
---
<img width="777" height="370" alt="Screenshot 2026-08-07 113335" src="https://github.com/user-attachments/assets/779dbb03-f39a-44ee-b799-e7ae9e27a751" />


```sql
CREATE TABLE Employees (
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1232" height="292" alt="Screenshot 2026-08-07 113412" src="https://github.com/user-attachments/assets/e4515cf3-f398-4bed-a148-e79f0b0f5226" />


**Question 4**
---
<img width="1030" height="320" alt="Screenshot 2026-08-07 113431" src="https://github.com/user-attachments/assets/af51144a-f55c-4124-a68e-5eee5017e5eb" />


```sql
CREATE TABLE Employees (
    EmployeeID INTEGER PRIMARY KEY,
    FirstName TEXT NOT NULL,
    LastName TEXT NOT NULL,
    Email TEXT UNIQUE,
    Salary REAL CHECK (Salary > 0),
    DepartmentID INTEGER,
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID)
);
```

**Output:**

<img width="1291" height="342" alt="Screenshot 2026-08-07 113458" src="https://github.com/user-attachments/assets/ecf60bb6-271f-4179-9a49-7ea4305f3c70" />


**Question 5**
---
<img width="1018" height="330" alt="Screenshot 2026-08-07 113519" src="https://github.com/user-attachments/assets/2c2b46c3-0c11-4ae9-8ff0-20d3e29d5f25" />


```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;

ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);
```

**Output:**

<img width="1185" height="303" alt="Screenshot 2026-08-07 113552" src="https://github.com/user-attachments/assets/f864b9bf-2b34-4bcb-ab71-ca1ba22de9fa" />


**Question 6**
---
<img width="795" height="365" alt="Screenshot 2026-08-07 113612" src="https://github.com/user-attachments/assets/2c42958a-3504-4923-b2c1-a91207133a86" />


```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');
```

**Output:**

<img width="896" height="297" alt="Screenshot 2026-08-07 113639" src="https://github.com/user-attachments/assets/57eeef28-f790-4921-93f5-819ecff61062" />


**Question 7**
---
<img width="752" height="282" alt="Screenshot 2026-08-07 113657" src="https://github.com/user-attachments/assets/081adc91-51e7-4588-a20e-d7c9f6e50bd2" />


```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

**Output:**

<img width="1217" height="241" alt="Screenshot 2026-08-07 113732" src="https://github.com/user-attachments/assets/1b6c6e02-2fb4-4237-a0cf-9050d40cac1a" />


**Question 8**
---
<img width="1152" height="322" alt="Screenshot 2026-08-07 113752" src="https://github.com/user-attachments/assets/0f524f5a-aa05-426a-b034-68d822670db5" />


```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (5, 'George Clark', 'Consultant', NULL, NULL);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (8, 'Ava Miller', 'Consultant', 'IT', NULL);
```

**Output:**
<img width="993" height="238" alt="Screenshot 2026-08-07 113817" src="https://github.com/user-attachments/assets/ef619a0e-f398-4040-8fe6-13e532697df9" />


**Question 9**
---
<img width="692" height="307" alt="Screenshot 2026-08-07 113835" src="https://github.com/user-attachments/assets/74115d2b-63ec-4c7c-84b5-6bdf9e8b596a" />


```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT(4),
    FOREIGN KEY (icom_id)
        REFERENCES company(com_id)
        ON UPDATE SET NULL
        ON DELETE SET NULL
);
```

**Output:**

<img width="1050" height="277" alt="Screenshot 2026-08-07 113904" src="https://github.com/user-attachments/assets/0d585e10-e215-4c1c-bbe8-7c54fa65ce56" />


**Question 10**
---
<img width="957" height="257" alt="Screenshot 2026-08-07 113919" src="https://github.com/user-attachments/assets/6d834f49-096d-4fab-b96b-acf6a3b3e84e" />


```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1160" height="177" alt="Screenshot 2026-08-07 113952" src="https://github.com/user-attachments/assets/3e64350a-bd0a-41dd-bccb-a91c0b34369e" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
