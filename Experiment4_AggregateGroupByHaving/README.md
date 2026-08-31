# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
<img width="553" height="585" alt="image" src="https://github.com/user-attachments/assets/51ea1608-e90b-4030-88cb-12c2267acb37" />


```sql
SELECT PatientID,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY PatientID;
```

**Output:**




**Question 2**
<img width="1028" height="652" alt="image" src="https://github.com/user-attachments/assets/3d2c681b-7bb3-4706-b7bc-a7880c1e6ae1" />


```sql
SELECT InsuranceCompany,
       COUNT(*) AS TotalExpiredPatients
FROM Insurance
WHERE ValidityPeriod < DATE('now')
GROUP BY InsuranceCompany;
```

**Output:**

<img width="917" height="832" alt="image" src="https://github.com/user-attachments/assets/e5576b2f-f5b2-45f2-845f-0c6a64cad239" />


**Question 3**
---
<img width="1020" height="565" alt="image" src="https://github.com/user-attachments/assets/4b73446b-c8c8-4ae2-ad3d-4b5cc399e701" />


```sql
SELECT DoctorID,
       strftime('%H:%M', AppointmentDateTime) AS TimeSlot,
       COUNT(*) AS TotalAppointments
FROM Appointments
GROUP BY DoctorID, TimeSlot
HAVING COUNT(*) = (
    SELECT MAX(cnt)
    FROM (
        SELECT COUNT(*) AS cnt
        FROM Appointments a2
        WHERE a2.DoctorID = Appointments.DoctorID
        GROUP BY strftime('%H:%M', a2.AppointmentDateTime)
    )
)
ORDER BY TotalAppointments DESC;
```

**Output:**

<img width="1047" height="745" alt="image" src="https://github.com/user-attachments/assets/b6944fb0-c362-45f3-b3b3-2bb459c994d1" />


**Question 4**
---
<img width="993" height="503" alt="image" src="https://github.com/user-attachments/assets/ec7dbf85-d13c-4761-b87c-abb4db66c5d5" />


```sql
SELECT COUNT(*) AS 'COUNT'
FROM customer
WHERE city = 'Noida';
```

**Output:**

<img width="520" height="391" alt="image" src="https://github.com/user-attachments/assets/3ea4db14-1521-4481-a510-bee8084ac29e" />


**Question 5**
<img width="858" height="472" alt="image" src="https://github.com/user-attachments/assets/39785b4e-cd0a-470e-b068-5c15d8a8cb03" />


```sql
SELECT AVG(income) AS avg_income
FROM employee
WHERE name LIKE 'A%';
```

**Output:**

<img width="451" height="405" alt="image" src="https://github.com/user-attachments/assets/741e0ad9-c94a-44ea-beb4-4f344475f1ea" />


**Question 6**
---
<img width="576" height="522" alt="image" src="https://github.com/user-attachments/assets/e7287913-3db4-462a-b8e2-978e5f1632fc" />

```sql
SELECT MAX(purch_amt) AS MAXIMUM
FROM orders;
```

**Output:**

<img width="453" height="392" alt="image" src="https://github.com/user-attachments/assets/38761621-a039-4d65-852e-9847569b3de6" />

**Question 7**
---
<img width="892" height="508" alt="image" src="https://github.com/user-attachments/assets/b7c19872-248e-46e8-a6fe-a450efa14c8c" />



```sql
SELECT COUNT(DISTINCT salesman_id) AS COUNT
FROM orders;
```

**Output:**

<img width="352" height="408" alt="image" src="https://github.com/user-attachments/assets/19dd71be-c69b-4a0e-aade-9179b8aa8fb5" />



**Question 8**
---
<img width="1150" height="455" alt="image" src="https://github.com/user-attachments/assets/6e032473-fc3d-46ba-a42f-e13daa8ce664" />


```sql
SELECT (age / 5) * 5 AS age_group,
       MIN(salary) AS "MIN(salary)"
FROM customer1
GROUP BY (age / 5) * 5
HAVING MIN(salary) < 2000;
```

**Output:**

<img width="640" height="411" alt="image" src="https://github.com/user-attachments/assets/5715e95b-6e48-455b-b838-c75f1cf7a04e" />


**Question 9**
---
<img width="1212" height="492" alt="image" src="https://github.com/user-attachments/assets/6fd6a34f-0ed5-452f-a3e8-75170b8027af" />


```sql
SELECT age, SUM(income) AS "SUM(income)"
FROM employee
GROUP BY age
HAVING SUM(income) > 1000000;
```

**Output:**

<img width="612" height="482" alt="image" src="https://github.com/user-attachments/assets/73adbc17-ef5c-4329-bf24-248854893f8c" />


**Question 10**
---
<img width="1190" height="450" alt="image" src="https://github.com/user-attachments/assets/33f2e988-df9b-4704-b46f-c06bcf2bdb44" />


```sql
SELECT address,
       AVG(salary) AS "AVG(salary)"
FROM customer1
GROUP BY address
HAVING AVG(salary) > 5000;
```

**Output:**

<img width="611" height="525" alt="image" src="https://github.com/user-attachments/assets/6a376046-b83a-4e09-8ef7-3a9db5a9ed77" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
