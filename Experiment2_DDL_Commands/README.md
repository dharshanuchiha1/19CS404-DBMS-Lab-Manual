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
<img width="1242" height="442" alt="image" src="https://github.com/user-attachments/assets/544de7f2-76c5-44d1-a7ef-bb66627cea80" />


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

<img width="1072" height="180" alt="image" src="https://github.com/user-attachments/assets/b1e07f95-7ee9-4738-be3d-1f84e1e5fd43" />


**Question 2**
---
<img width="1287" height="317" alt="image" src="https://github.com/user-attachments/assets/409eae81-60df-480f-843e-f7f69527251e" />


```sql
ALTER TABLE Companies
ADD COLUMN designation varchar(50);

ALTER TABLE Companies
ADD COLUMN net_salary number;
```

**Output:**

<img width="1157" height="292" alt="image" src="https://github.com/user-attachments/assets/e77dd726-facc-4d3d-8810-7c532ce77a2d" />

**Question 3**
---
<img width="777" height="370" alt="image" src="https://github.com/user-attachments/assets/956fc47c-882c-4926-accd-4c17467bb551" />


```sql
CREATE TABLE Employees (
    EmployeeID INTEGER,
    FirstName TEXT,
    LastName TEXT,
    HireDate DATE
);
```

**Output:**

<img width="1232" height="292" alt="image" src="https://github.com/user-attachments/assets/cff6d40a-0861-4831-80a4-b06647b45feb" />


**Question 4**
---
<img width="1030" height="320" alt="image" src="https://github.com/user-attachments/assets/352720e7-82df-4a36-8830-144a4af08a4b" />


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

<img width="1291" height="342" alt="image" src="https://github.com/user-attachments/assets/9058c815-384b-42a3-a1ea-885b6588d43f" />


**Question 5**
---
<img width="1018" height="330" alt="image" src="https://github.com/user-attachments/assets/9535a9ba-8035-44b1-9baf-d7ce669d8374" />


```sql
ALTER TABLE Student_details
ADD COLUMN MobileNumber NUMBER;

ALTER TABLE Student_details
ADD COLUMN Address VARCHAR(100);

```

**Output:**

<img width="1185" height="303" alt="image" src="https://github.com/user-attachments/assets/245a9a52-d66a-4d6d-ad24-5b67fe520617" />


**Question 6**
---
<img width="795" height="365" alt="image" src="https://github.com/user-attachments/assets/5b3f89ce-ff78-4ffa-acee-d529020a9bc2" />


```sql
INSERT INTO Student_details (RollNo, Name, Gender)
VALUES (204, 'Samuel Black', 'M');
```

**Output:**

<img width="896" height="297" alt="image" src="https://github.com/user-attachments/assets/1fa82856-76d3-411d-8e46-d828f4546c74" />

**Question 7**
---
<img width="752" height="282" alt="image" src="https://github.com/user-attachments/assets/60a895eb-a364-4b11-8d5f-e3b13f646a43" />


```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, YearPublished)
SELECT ISBN, Title, Author, Publisher, YearPublished
FROM Out_of_print_books;
```

**Output:**

<img width="1217" height="241" alt="image" src="https://github.com/user-attachments/assets/fa6ce80d-ae23-418e-99a7-d524ae01cfd9" />


**Question 8**
---
<img width="1152" height="322" alt="image" src="https://github.com/user-attachments/assets/d46b416f-de61-4c1a-a3af-ba0e6a3da35f" />


```sql
INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (5, 'George Clark', 'Consultant', NULL, NULL);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (7, 'Noah Davis', 'Manager', 'HR', 60000);

INSERT INTO Employee (EmployeeID, Name, Position, Department, Salary)
VALUES (8, 'Ava Miller', 'Consultant', 'IT', NULL);
```

**Output:**

<img width="993" height="238" alt="image" src="https://github.com/user-attachments/assets/4a7e718c-d4e2-469c-9a1a-4f9613b04738" />


**Question 9**
---
<img width="692" height="307" alt="image" src="https://github.com/user-attachments/assets/474362af-969b-418c-af6c-ce66a49779d9" />


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

<img width="1050" height="277" alt="image" src="https://github.com/user-attachments/assets/cf85c976-804d-40ee-b381-3d01b67ca7bf" />


**Question 10**
---
<img width="957" height="257" alt="image" src="https://github.com/user-attachments/assets/238b382f-0d8f-4855-a5cb-27cb8272887b" />


```sql
CREATE TABLE Products (
    ProductID INTEGER PRIMARY KEY,
    ProductName TEXT UNIQUE NOT NULL,
    Price REAL CHECK (Price > 0),
    StockQuantity INTEGER CHECK (StockQuantity >= 0)
);
```

**Output:**

<img width="1160" height="177" alt="image" src="https://github.com/user-attachments/assets/08cb9aa4-6379-4e47-a515-96e03dbeb82f" />



## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
