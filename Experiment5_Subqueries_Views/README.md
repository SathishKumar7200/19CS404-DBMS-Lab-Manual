# Experiment 5: Subqueries and Views

## AIM
To study and implement subqueries and views.

## THEORY

### Subqueries
A subquery is a query inside another SQL query and is embedded in:
- WHERE clause
- HAVING clause
- FROM clause

**Types:**
- **Single-row subquery**:
  Sub queries can also return more than one value. Such results should be made use along with the operators in and any.
- **Multiple-row subquery**:
  Here more than one subquery is used. These multiple sub queries are combined by means of ‘and’ & ‘or’ keywords.
- **Correlated subquery**:
  A subquery is evaluated once for the entire parent statement whereas a correlated Sub query is evaluated once per row processed by the parent statement.

**Example:**
```sql
SELECT * FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
### Views
A view is a virtual table based on the result of an SQL SELECT query.
**Create View:**
```sql
CREATE VIEW view_name AS
SELECT column1, column2 FROM table_name WHERE condition;
```
**Drop View:**
```sql
DROP VIEW view_name;
```

**Question 1**
--
<img width="1283" height="653" alt="image" src="https://github.com/user-attachments/assets/ae633544-5548-40ea-80e3-0005489776ef" />


```sql
select *
from GRADES
where grade=(
    select MIN(grade)
    from GRADES as g2
    where g2.subject=GRADES.subject
    );
```

**Output:**

<img width="1217" height="449" alt="image" src="https://github.com/user-attachments/assets/252734fe-7349-4e2c-9847-f601d019db4e" />


**Question 2**
---
<img width="1273" height="692" alt="image" src="https://github.com/user-attachments/assets/596efd37-d8b3-4e81-bb2c-ce98c80e351d" />


```sql
select *
from CUSTOMERS
where SALARY IN(
    select SALARY
    from CUSTOMERS
    where SALARY>4500
    );
```

**Output:**

<img width="1223" height="427" alt="image" src="https://github.com/user-attachments/assets/6cf9d50a-32ca-4984-a5bd-5febb9d6be0f" />


**Question 3**
---
<img width="1281" height="829" alt="image" src="https://github.com/user-attachments/assets/e87322fe-7dd6-44f4-9915-a9238cea8111" />


```sql
SELECT ord_no, purch_amt, ord_date, salesman_id
FROM orders
WHERE salesman_id IN (
    SELECT salesman_id
    FROM salesman
    WHERE commission = (SELECT MAX(commission) FROM salesman)
);

```

**Output:**

<img width="1175" height="452" alt="image" src="https://github.com/user-attachments/assets/b5fa2b64-57f7-4b62-9a0d-e8055589dc76" />


**Question 4**
---
<img width="1257" height="623" alt="image" src="https://github.com/user-attachments/assets/a6371c48-4da3-4597-89f2-3d5d85e918cd" />


```sql
SELECT *
FROM CUSTOMERS
WHERE ADDRESS = 'Delhi'
AND AGE < 30
ORDER BY ID;

```

**Output:**

<img width="1239" height="343" alt="image" src="https://github.com/user-attachments/assets/386d4b7a-6615-44f5-9e72-9a390927a00e" />


**Question 5**
---
<img width="1074" height="681" alt="image" src="https://github.com/user-attachments/assets/559c5e91-cf12-4677-85cc-7e9d4a0f84a3" />


```sql
select *
from CUSTOMERS
where SALARY<(
    select 2500
    );
```

**Output:**

<img width="1226" height="432" alt="image" src="https://github.com/user-attachments/assets/5909c18f-879a-4d8e-9307-b609f6842fdd" />


**Question 6**
---
<img width="1132" height="522" alt="image" src="https://github.com/user-attachments/assets/9fc89fa2-c13b-4ae1-bf70-5a63c4b204b1" />


```sql
select *
from Medications
where dosage =(
    select MIN(dosage)
    from Medications
   
    );
```

**Output:**

<img width="988" height="390" alt="image" src="https://github.com/user-attachments/assets/b44c0820-5233-4845-9489-ebf651647253" />


**Question 7**
---
<img width="1152" height="757" alt="image" src="https://github.com/user-attachments/assets/cf2eafc5-b362-4bf7-9a3f-f9e8957599a9" />


```sql
SELECT *
FROM CUSTOMERS
WHERE AGE IN (
    SELECT AGE
    FROM CUSTOMERS
    WHERE AGE < 30
);

```

**Output:**

<img width="1221" height="569" alt="image" src="https://github.com/user-attachments/assets/16ce5550-785e-41d8-803a-35559cadee5e" />


**Question 8**
---
<img width="1268" height="617" alt="image" src="https://github.com/user-attachments/assets/be9110a6-788a-4328-af73-8c3e9ed4e754" />


```sql
SELECT *
FROM Employee
WHERE age < (
    SELECT AVG(age)
    FROM Employee
    WHERE income > 1000000
);

```

**Output:**

<img width="690" height="395" alt="image" src="https://github.com/user-attachments/assets/057abcc9-e976-4fc2-91e6-8bf59b552db7" />

<img width="686" height="415" alt="image" src="https://github.com/user-attachments/assets/fe222f8a-e0a7-423a-ad75-3dc9112a3612" />

**Question 9**
---
<img width="1167" height="560" alt="image" src="https://github.com/user-attachments/assets/d9f22962-48bd-4554-8a04-42c18c47e7da" />


```sql
SELECT name, city
FROM customer
WHERE city IN (
    SELECT city
    FROM customer
    WHERE id IN (3, 7)
);

```

**Output:**

<img width="801" height="438" alt="image" src="https://github.com/user-attachments/assets/d0ea2a0a-4254-46cd-8d0b-09eedf95d3cf" />


**Question 10**
---
<img width="1169" height="650" alt="image" src="https://github.com/user-attachments/assets/e2849872-e995-4f36-b22b-b9db624a00de" />


```sql
select *
from CUSTOMERS
where ADDRESS in (
    select ADDRESS 
    from CUSTOMERS
    where ADDRESS='Delhi'
    );
```

**Output:**

<img width="1214" height="312" alt="image" src="https://github.com/user-attachments/assets/80eeedaa-5176-421b-8bef-acbde78e053e" />



## RESULT
Thus, the SQL queries to implement subqueries and views have been executed successfully.
