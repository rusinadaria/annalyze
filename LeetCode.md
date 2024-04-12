## 175
```sql
SELECT firstName, lastName, Address.city, Address.state FROM Person
LEFT JOIN Address ON Address.personID = Person.personId
```
## 176
```sql
SELECT (
    SELECT salary as SecondHighestSalary FROM Employee
    WHERE id = 2 AND id IS NOT NULL
)
```
## 177
```sql
CREATE OR REPLACE FUNCTION NthHighestSalary(N INT) RETURNS TABLE (Salary INT) AS $$
BEGIN
  RETURN QUERY (
    -- Write your PostgreSQL query statement below.
    SELECT DISTINCT tab.salary as getNthHighestSalary FROM (
	SELECT dense_rank() over (order by employee.salary desc) as rank, employee.* from employee
    ) as tab
    WHERE rank = N
  );
END;
$$ LANGUAGE plpgsql;
```
## 178
```sql
SELECT score, dense_rank() over(order by score desc) rank FROM Scores
```
## 182
```sql
SELECT email as Email FROM Person
GROUP BY Email
HAVING COUNT(Email)>1
```
