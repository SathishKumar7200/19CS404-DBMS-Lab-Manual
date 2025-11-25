# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1267" height="703" alt="image" src="https://github.com/user-attachments/assets/07d5b8d2-e530-4784-a28d-16d78a16a031" />


```sql
SELECT p.*
FROM patients AS p
INNER JOIN appointments AS a
ON p.patient_id = a.patient_id
WHERE a.appointment_date BETWEEN '2024-01-01' AND '2024-01-31';

```

**Output:**

<img width="1066" height="401" alt="image" src="https://github.com/user-attachments/assets/314d94b7-a276-4a89-a57b-0cae6d1cd53e" />

<img width="1061" height="405" alt="image" src="https://github.com/user-attachments/assets/2e1c8234-9cce-47cf-a360-40035d541acc" />

**Question 2**
---
<img width="1277" height="776" alt="image" src="https://github.com/user-attachments/assets/06c82f0b-f100-41a0-8a6f-aab57873d3c3" />

<img width="1126" height="761" alt="image" src="https://github.com/user-attachments/assets/a974a8d8-1a9e-4ea2-992f-e3418549464d" />

```sql
SELECT 
    o.ord_no,
    o.ord_date,
    o.purch_amt,
    c.cust_name AS "Customer Name",
    c.grade,
    s.name AS "Salesman",
    s.commission
FROM orders AS o
INNER JOIN customer AS c
    ON o.customer_id = c.customer_id
INNER JOIN salesman AS s
    ON o.salesman_id = s.salesman_id;
```

**Output:**

<img width="985" height="783" alt="image" src="https://github.com/user-attachments/assets/163cef56-605e-49e8-aa8e-8d7534dc830b" />

<img width="992" height="763" alt="image" src="https://github.com/user-attachments/assets/44d504ba-3fb9-45e2-a2c4-995454ca4425" />

**Question 3**
---
<img width="1185" height="377" alt="image" src="https://github.com/user-attachments/assets/7a0267bb-b6bc-487a-9da9-4b06c07a8b7b" />


```sql
SELECT c.*
FROM customer AS c
LEFT JOIN orders AS o
ON c.customer_id = o.customer_id
WHERE o.ord_date BETWEEN '2012-07-01' AND '2012-07-30';
```

**Output:**

<img width="790" height="402" alt="image" src="https://github.com/user-attachments/assets/17a85b3a-c7a7-42b3-bab5-8d1a6669d03a" />

<img width="781" height="405" alt="image" src="https://github.com/user-attachments/assets/0c1e8bab-cdd2-43db-a6f6-d8538159ad49" />

**Question 4**
---
<img width="1095" height="886" alt="image" src="https://github.com/user-attachments/assets/138ddd41-4deb-4415-88d9-a5d3354bbf76" />


```sql
SELECT s.name AS Salesman, 
       c.cust_name, 
       s.city
FROM salesman AS s
INNER JOIN customer AS c
ON s.city = c.city;

```

**Output:**

<img width="1070" height="681" alt="image" src="https://github.com/user-attachments/assets/827072f8-f469-471c-ac79-21a94a82a7ae" />


**Question 5**
---
<img width="1281" height="980" alt="image" src="https://github.com/user-attachments/assets/90985ede-adb8-4f50-93f8-ae659b332f08" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city,
    s.name AS "Salesman",
    s.commission
FROM customer AS c
INNER JOIN salesman AS s
ON c.salesman_id = s.salesman_id;

```

**Output:**

<img width="670" height="852" alt="image" src="https://github.com/user-attachments/assets/cd11fc96-ac63-4f3a-9c3a-c317be855afe" />

<img width="681" height="909" alt="image" src="https://github.com/user-attachments/assets/7a25dde2-1fb8-4642-9dd9-8d624b3cc4e8" />

**Question 6**
---
<img width="1292" height="379" alt="image" src="https://github.com/user-attachments/assets/da2520cf-1f7e-4d0a-86d1-80610e37da7b" />


```sql
SELECT 
    c.cust_name, 
    s.name
FROM customer AS c
LEFT JOIN salesman AS s
ON c.salesman_id = s.salesman_id
where c.city = s.city;
```

**Output:**

<img width="817" height="545" alt="image" src="https://github.com/user-attachments/assets/d1022803-344d-42a5-b13b-68d221b0c79a" />


**Question 7**
---
<img width="1257" height="715" alt="image" src="https://github.com/user-attachments/assets/45e2e29f-c162-4a84-bf68-388ae13d0cec" />


```sql
SELECT p.first_name AS patient_name
FROM patients AS p
INNER JOIN doctors AS d
ON p.doctor_id = d.doctor_id
WHERE d.first_name = 'Emily'
  AND d.last_name = 'Johnson'
  AND p.discharge_date IS NOT NULL;

```

**Output:**

<img width="582" height="390" alt="image" src="https://github.com/user-attachments/assets/5e80841c-d8ec-478c-aba2-b437fd4637a7" />


**Question 8**
---
<img width="1275" height="785" alt="image" src="https://github.com/user-attachments/assets/ce3ba635-2d04-4b29-8c3c-38c158adbc65" />

<img width="1262" height="757" alt="image" src="https://github.com/user-attachments/assets/b76a054a-91a6-4aaf-a2ef-b37d2bf61ed4" />


```sql
SELECT 
    o.ord_no,
    o.purch_amt,
    o.ord_date,
    c.cust_name,
    c.city AS customer_city,
    c.grade,
    s.name AS salesman_name,
    s.city AS salesman_city,
    s.commission
FROM orders AS o
INNER JOIN customer AS c
    ON o.customer_id = c.customer_id
INNER JOIN salesman AS s
    ON o.salesman_id = s.salesman_id;

```

**Output:**

<img width="1054" height="418" alt="image" src="https://github.com/user-attachments/assets/f05b7ceb-b20d-4d11-987f-d196c41542c9" />

<img width="254" height="403" alt="image" src="https://github.com/user-attachments/assets/346afb56-6c13-4329-ac9b-68c93b80a747" />

<img width="983" height="416" alt="image" src="https://github.com/user-attachments/assets/a9322351-1a84-4119-bfd1-36d7b497fab1" />

<img width="314" height="397" alt="image" src="https://github.com/user-attachments/assets/05aba04c-ae9e-4cb8-865a-90f5ffcb4b37" />

**Question 9**
---
<img width="1237" height="945" alt="image" src="https://github.com/user-attachments/assets/fcdcdafd-d675-4e05-95a2-de8540090b97" />


```sql
SELECT 
    c.cust_name AS "Customer Name",
    c.city AS "city",
    s.name AS "Salesman",
    s.commission
FROM customer AS c
INNER JOIN salesman AS s
ON c.salesman_id = s.salesman_id
WHERE s.commission > 0.12;

```

**Output:**

<img width="676" height="760" alt="image" src="https://github.com/user-attachments/assets/11f0f020-f6f6-47d9-80be-d80057cf32b2" />

<img width="665" height="753" alt="image" src="https://github.com/user-attachments/assets/1c19ec05-7c63-43c5-b906-2818110224f9" />

**Question 10**
---
<img width="1274" height="853" alt="image" src="https://github.com/user-attachments/assets/4048eb27-7235-4e91-99a1-f941ba65cc21" />


```sql
SELECT 
    p.*,
    d.first_name AS doctor_name
FROM patients AS p
INNER JOIN doctors AS d
ON p.doctor_id = d.doctor_id;

```

**Output:**

<img width="1179" height="534" alt="image" src="https://github.com/user-attachments/assets/a0e720e9-726c-4b08-9b34-e344a7896ca4" />

<img width="1188" height="552" alt="image" src="https://github.com/user-attachments/assets/bd3adf91-6415-4f2e-871a-0d372623198a" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
