# Experiment 3: DML Commands

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
--
<img width="884" height="816" alt="image" src="https://github.com/user-attachments/assets/05f53931-5026-44ea-91d6-1ed564d1aa5d" />


```sql
UPDATE SALES
SET sell_price = sell_price + 3
WHERE product_id IN (
    SELECT product_id
    FROM PRODUCTS
    WHERE supplier_id = 4
);
```

**Output:**

<img width="997" height="228" alt="image" src="https://github.com/user-attachments/assets/40acb2ee-67bf-4cba-8a37-d0942141343b" />


**Question 2**
---
<img width="476" height="120" alt="image" src="https://github.com/user-attachments/assets/15aa8ce7-ee2a-4ff9-83d5-45d1c90579e3" />


```sql
UPDATE products
SET product_name = 'Grapefruit'
WHERE product_id = 4;
```

**Output:**

<img width="657" height="158" alt="image" src="https://github.com/user-attachments/assets/eab5d687-6b93-4e89-86f9-762dd358c68a" />


**Question 3**
---
<img width="383" height="55" alt="image" src="https://github.com/user-attachments/assets/c4e77d26-01b3-41a0-adf2-cae507e0717d" />


```sql
UPDATE Customer
SET grade = 5
WHERE city = 'Chennai';
```

**Output:**

<img width="858" height="270" alt="image" src="https://github.com/user-attachments/assets/23f84d71-9dae-4834-af25-99e7bf91df9f" />


**Question 4**
---
<img width="506" height="255" alt="image" src="https://github.com/user-attachments/assets/71863fe6-5a11-4306-bb57-7ccb1da1553d" />


```sql
UPDATE suppliers
SET address = '58 Lakeview, Magnolia'
WHERE supplier_id = 5;
```

**Output:**

<img width="1340" height="238" alt="image" src="https://github.com/user-attachments/assets/6382c8e0-4fc9-41a3-a41a-ad80d5943ed0" />


**Question 5**
---
<img width="653" height="230" alt="image" src="https://github.com/user-attachments/assets/023a8ac9-bb0b-4bc8-b778-996460e13fc8" />


```sql
UPDATE products
SET reorder_lvl = 20
WHERE quantity < 10
  AND category = 'Snacks';
```

**Output:**

<img width="1193" height="325" alt="image" src="https://github.com/user-attachments/assets/9f43f92a-afe0-4aec-8574-9989247371aa" />


**Question 6**
---
<img width="936" height="344" alt="image" src="https://github.com/user-attachments/assets/82ef1617-bf08-4f2e-b8f9-9ac7f6362879" />


```sql
DELETE FROM customer
WHERE cust_city LIKE 'L%';
```

**Output:**

<img width="1223" height="394" alt="image" src="https://github.com/user-attachments/assets/d6b61d51-4767-43a7-aae1-0ed27c6717ad" />


**Question 7**
---
<img width="758" height="342" alt="image" src="https://github.com/user-attachments/assets/a2f8aaf2-a691-485d-8066-dd174aef6322" />


```sql
DELETE FROM customer
WHERE GRADE < 2;
```

**Output:**

<img width="359" height="314" alt="image" src="https://github.com/user-attachments/assets/564a9e9e-75ae-4497-a5fe-cf0b528f206c" />


**Question 8**
---
<img width="674" height="265" alt="image" src="https://github.com/user-attachments/assets/ca0b7611-9133-4d83-a6dc-30c1fa8db9f8" />


```sql
DELETE FROM doctors
WHERE last_name = 'Brown'
  AND specialization IN ('Pediatrics', 'Cardiology');
```

**Output:**

<img width="646" height="509" alt="image" src="https://github.com/user-attachments/assets/9ac464dd-5ad9-46ed-85b2-96274041cbad" />


**Question 9**
---
<img width="767" height="240" alt="image" src="https://github.com/user-attachments/assets/5ad207a3-a3c1-4ad4-adcd-29ce28dfb2d6" />


```sql
DELETE FROM customer
WHERE (GRADE = 3 OR AGENT_CODE = 'A008')
  AND OUTSTANDING_AMT < 5000;
```

**Output:**

<img width="1054" height="165" alt="image" src="https://github.com/user-attachments/assets/7a8cf6d8-2d0a-456d-a199-9c3466421183" />


**Question 10**
---
<img width="375" height="289" alt="image" src="https://github.com/user-attachments/assets/250b0992-3bf6-441c-97d2-630ed3eceb2c" />


```sql
DELETE FROM doctors
WHERE specialization IS NULL;
```

**Output:**

<img width="637" height="549" alt="image" src="https://github.com/user-attachments/assets/28ee8f43-4a99-4dba-b717-c63712d6a91c" />

**Grade:**

<img width="558" height="203" alt="image" src="https://github.com/user-attachments/assets/40610d07-d705-489d-9f30-b5f236a7b4cb" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
