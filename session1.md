# LAB 1 : Basic SQL queries
### 18-07-2024

## Questions & Answers

**1. How to install mySQL**

```bash
sudo apt install mysql-server

```

**2. Finding year from given date**

```mySQL
SELECT YEAR(my_date) AS year_value

```
![image](https://github.com/user-attachments/assets/42c19469-48da-4db3-9cd2-e32accc2a54a)


**3. Check whether date is of given format**

```mySQL
SELECT
    CASE
        WHEN '18-07-2024' REGEXP '^[0-9]{2}-[0-9]{2}-[0-9]{4}$' THEN 'Valid'
        ELSE 'Invalid'
    END AS date_status;

```
![image](https://github.com/user-attachments/assets/6ae46e6a-c1ba-4356-bfcd-eba734899537)

**4. Retrieve next date**

```mySQL
SELECT DATE_ADD("2024-07-18", INTERVAL 1 DAY);
```
![image](https://github.com/user-attachments/assets/c10f1c72-77b3-42cf-8fed-4f4bd1714956)


**5. Retrive user name and password**

N/A


**6. Get database date**

```mySQL
SELECT CURRENT_TIMESTAMP();
```

![image](https://github.com/user-attachments/assets/efc2b724-39f7-4766-bfce-f563a15f65ba)


**7. Get default database name**

```mySQL
USE mysql;
```



**8. Get host and user name**

```mySQL
SELECT Host, User FROM mysql.user
```
![image](https://github.com/user-attachments/assets/e0485cd9-8eee-4e84-ba7a-6973ed7427b0)


**9. Get mySQL server version**

```mySQL
mysql --V
```

**10. Bitwise XOR, AND, OR**

Use bitwise operators: 

```mySQL
SELECT 1&2 AS andRes, 1|2 AS orRes, 1^2 AS xorRes;
```
![image](https://github.com/user-attachments/assets/ab5dcf1d-525f-42b5-bc4a-8e969dd9574c)


**11. Find difference between two given dates**
```mySQL
SELECT DATEDIFF("date1", "date1) AS result;
```

![image](https://github.com/user-attachments/assets/db8b8617-c1a5-45a8-b61b-8708a46e316a)


**12. Add 2 hrs 50 min to current time**

```mySQL
SELECT ADDTIME("currtime", "02:50:00") AS updated;
```

![image](https://github.com/user-attachments/assets/57dd69be-de65-4e5a-93cb-fade6c7e5558)


**13. Floor and Ceil of a given decimal value**

```mySQL
select floor(9.8) as f, ceil(9.8) as c;
```

![image](https://github.com/user-attachments/assets/61f40e0e-ccf7-4bcc-a7b3-75efb5084d04)


**14. Do operations on Regex**
```mySQL
select "Krishna Keerthana" REGEXP "A*";
select "Krishna Keerthana" REGEXP "B+";

```

![image](https://github.com/user-attachments/assets/399a8d1e-bd40-4173-88fe-c5c0c0865103)


**15. Compare 2 strings**

```mySQL
Select STRCMP('Kkay', 'Kkay') As 'Cmp_Value';
```

![image](https://github.com/user-attachments/assets/58a6864c-46e9-470f-8962-37cd18e83436)


**16. Implement a grading system**

This can be done by creating a data table:

```mySQL
-- Create a sample table
CREATE TABLE students (
    student_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    marks INT
);

-- Insert sample data
INSERT INTO students (name, marks) VALUES
    ('John Doe', 85),
    ('Jane Smith', 70),
    ('Alice Johnson', 95),
    ('Bob Brown', 60),
    ('Eve Lee', 45);

-- Query to simulate grading system
SELECT 
    student_id,
    name,
    marks,
    CASE
        WHEN marks >= 90 THEN 'A'
        WHEN marks >= 80 THEN 'B'
        WHEN marks >= 70 THEN 'C'
        WHEN marks >= 60 THEN 'D'
        ELSE 'F'
    END AS grade
FROM students;
```

![image](https://github.com/user-attachments/assets/95f2e3f0-d72e-431c-8c5a-8d85e02d0263)


**17. Explore IFNULL()**

The function IFNULL() is used in SQL to check if any table values are null. The basic syntax for this function is:

```mySQL
IFNULL(expression, alt_value)
```
- Expression: Checks for a particular value(column) in the database table
- Alt_value : Replaces NULL values with a given value

For example:

```mySQL

SELECT employee_id, name, IFNULL(commision, 0) AS commission
FROM employees;
```

Let's see how this works on a table

Before:-

| employee_id | name          | commission |
|-------------|---------------|------------|
| 101         | Alice Johnson | 500.00     |
| 102         | Bob Smith     | NULL       |
| 103         | Carol Davis   | 250.00     |
| 104         | David Brown   | NULL       |
| 105         | Emily Clark   | 300.00     |

After the function statements are carried out:-

| employee_id | name          | commission |
|-------------|---------------|------------|
| 101         | Alice Johnson | 500.00     |
| 102         | Bob Smith     | 0.00       |
| 103         | Carol Davis   | 250.00     |
| 104         | David Brown   | 0.00       |
| 105         | Emily Clark   | 300.00     |



**18. Grant all access perms to a user**
```mySQL
GRANT ALL PRIVILEGES ON database_name.* TO 'username'@'localhost';
```


**19. Show all databses**

```mySQL
show databases;
```

![image](https://github.com/user-attachments/assets/df769509-6d81-4d37-9945-4e1772feb5f4)


**20. Size of schema**

```mySQL
SELECT
SUM(ROUND(((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024), 2)) AS "SIZE IN MB"
FROM INFORMATION_SCHEMA.TABLES
WHERE
TABLE_SCHEMA = "SCHEMA-NAME";
```
