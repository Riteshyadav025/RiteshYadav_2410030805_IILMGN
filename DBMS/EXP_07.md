### 1.Compute the no. of days remaining in this year.
 ~~~sql
SELECT (TO_DATE(EXTRACT(YEAR FROM SYSDATE) || '-12-31', 'YYYY-MM-DD') - SYSDATE) AS days_remaining
FROM dual;
~~~

### 2. Find the highest and lowest salaries and the difference between of them.
~~~sql
SELECT 
    MAX(sal) AS highest_salary,
    MIN(sal) AS lowest_salary,
    MAX(sal) - MIN(sal) AS difference
FROM emp;
~~~

### 3. List employee whose commission is greater than 25 % of their salaries.
~~~sql
ELECT ename, sal, comm
FROM emp
WHERE comm > 0.25 * sal;
~~~

### 4. Make a query that displays salary in dollar format.
~~~sql
SELECT ename, TO_CHAR(sal, '$999,999.00') AS salary_in_dollars
FROM emp;
~~~

### 5. Create a matrix query to display the job, the salary for that job based on department number, and the total salary for that job for all departments, giving each column an appropriate heading.
~~~sql
SELECT 
    job,
    SUM(CASE WHEN deptno = 10 THEN sal END) AS dept_10,
    SUM(CASE WHEN deptno = 20 THEN sal END) AS dept_20,
    SUM(CASE WHEN deptno = 30 THEN sal END) AS dept_30,
    SUM(sal) AS total_salary
FROM emp
GROUP BY job;
~~~

### 6. Query that will display the total no of employees, and of that total the number who were hired in 1980,1981,1982 and 1983. Give appropriate column heading.
~~~sql
SELECT 
    COUNT(*) AS total_employees,
    SUM(CASE WHEN EXTRACT(YEAR FROM hiredate) = 1980 THEN 1 ELSE 0 END) AS "1980",
    SUM(CASE WHEN EXTRACT(YEAR FROM hiredate) = 1981 THEN 1 ELSE 0 END) AS "1981",
    SUM(CASE WHEN EXTRACT(YEAR FROM hiredate) = 1982 THEN 1 ELSE 0 END) AS "1982",
    SUM(CASE WHEN EXTRACT(YEAR FROM hiredate) = 1983 THEN 1 ELSE 0 END) AS "1983"
FROM emp;
~~~

### 7. Query to get the last Sunday of Any Month.
~~~sql
SELECT 
    NEXT_DAY(LAST_DAY(SYSDATE) - 7, 'SUNDAY') AS last_sunday
FROM dual;
~~~

### 8. Display department numbers and total number of employees working in each department.
~~~sql
SELECT deptno, COUNT(*) AS total_employees
FROM emp
GROUP BY deptno;
~~~

### 9. Display the various jobs and total number of employees within each job group.
~~~sql
SELECT job, COUNT(*) AS total_employees
FROM emp
GROUP BY job;
~~~

### 10. Display the depart numbers and total salary for each department. give a code for vs code.
~~~sql
SELECT deptno, SUM(sal) AS total_salary
FROM emp
GROUP BY deptno;
~~~
